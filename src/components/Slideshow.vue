<template>
  <div>
    <v-carousel cycle height="100%" show-arrows-on-hover>
        <v-carousel-item v-for="(img, i) in imgs" :key="i" eager>
            <v-img height="100%" :src="img" eager/>
        </v-carousel-item>
    </v-carousel>
  </div>
</template>

<script>
export default {
  name: "Slideshow",
  
  data: () => 
  ({
      imgs:[],
  }),
  
  created() 
  {
    this.importAll(require.context('@/assets/slideshow/', true, /\.(jpg|png|svg)$/))
  },

  methods: 
  {
    importAll(r) 
    {
      r.keys().forEach(key =>(this.imgs.push({ src: r(key) })));
    }
  },
};
</script>