<template>

<v-div>

    <!--This is the PopUp that hold Contact Form-->
  <v-div class = "darkbackground" :style="{display: popUp}">
    <div class = "whitebackground">
      <div class="close" @click="closeOnClicked">
        <h3>+</h3>
      </div>

      <ContactFormPopUp/>

    </div>
  </v-div>


<v-card>


<v-app-bar  ref="appBarRef"  app  color="primary"  dark>

    <div>
        <v-img  alt="CPP Logo"  class="shrink mr-2 logo"  contain  :src="require('@/assets/logo.png')"/>
    </div>

    <v-spacer></v-spacer>

    <div v-if="displayHamburger">
        <v-app-bar-nav-icon  @click.stop="drawer=!drawer"></v-app-bar-nav-icon>
    </div>

    <div v-else> 
        <v-btn  @click="jumpToElement('idAbout')"  text>
            <span>About</span>     
        </v-btn>

        <v-btn  @click="jumpToElement('idCompetitions')"  text>
            <span>Competitions</span>       
        </v-btn>
        
        <v-btn  @click="jumpToElement('idSponsors')"  text>
            <span>Sponsors</span>       
        </v-btn>

        <v-btn  @click="jumpToElement('idDonate')"  text>
            <span>Donate</span>
        </v-btn>
      
        <v-btn  @click="contactOnClicked"  text>
            <span>Contact</span>  
        </v-btn>
    </div>     
</v-app-bar>

<v-navigation-drawer  v-model="drawer"  v-if="displayHamburger"  color="primary"  width="160"    right  temporary  >
        <br><br>
        <v-btn  @click="jumpToElement('idAbout')"  text>
            <span>About</span>       
        </v-btn>
        <br><br>
        
        <v-btn  @click="jumpToElement('idCompetitions')"  text>
            <span>Competitions</span>       
        </v-btn>
        <br><br>
        
        <v-btn  @click="jumpToElement('idSponsors')"  text>
            <span>Sponsors</span>       
        </v-btn>
        <br><br>
        
        <v-btn  @click="jumpToElement('idDonate')"  text>
            <span>Donate</span>
        </v-btn>
        <br><br>
        
        <v-btn  @click="contactOnClicked"  text>
            <span>Contact</span>  
        </v-btn>
</v-navigation-drawer>
</v-card>


</v-div>
</template>

<script>
import ContactFormPopUp from './ContactFormPopUp';


export default 
{

    name: "Menu",
    data: () =>
    ({
        displayHamburger: false,
        drawer: false,
        popUp: "none",
    }),
    methods:
    {
        checkBarWidth()
        {
            this.displayHamburger = window.innerWidth < 800;
        },
        
        jumpToElement(idTarget)
        {
           // document.getElementById(idTarget).scrollIntoView() has issues with an offset scroll. The "-55" corrects this.
           // This -55 may or may not need to be further tweaked after future changes.
           const y = document.getElementById(idTarget).getBoundingClientRect().top + window.pageYOffset - 55;
           
           // Note: smooth scroll currently doesn't seem to work on mobile (it still scrolls, just not smoothly).
           // Not really an issue, but would be cool if someone knew how to make it work.
           window.scrollTo({top: y, behavior: 'smooth'});
           if(this.drawer)
                this.drawer = false;
        },
        contactOnClicked()
        {
          this.popUp = "flex";
        },
        closeOnClicked()
        {
          this.popUp = "none";
        }
    },
    components: 
    {
        ContactFormPopUp,
    },

  
    mounted()
    {
        window.addEventListener('resize', this.checkBarWidth);
        this.checkBarWidth();
    },
    
    beforeDestroy()
    {
        window.removeEventListener('resize', this.checkBarWidth);
    },


    
};
</script>



<style>
    .logo{width: 13em;}

    .darkbackground{
      width: 100%;
      height: 100%;
      position: absolute;
      background-color: rgba(0,0,0,0.7);
      z-index: 20;
    }
    .whitebackground{
      left: 50%;
      top: 20%;
      position: relative;
      width: 500px;
      height: 640px;
      display: inline-block;
      background-color: #F7F7F7;
      z-index:5;
      transform: translate(-50%,-50%);
      text-align: center;
      border-radius: 15px;
      box-shadow: 0px 0p  x 12px rgba(0,0,0,0.3);
      overflow-x: hidden;
      overflow-y: auto;

    }
    .close{
      height:20px;
      margin:10px;
    }
    h3{
      cursor:pointer;
      font-size: 30px;
      float: right;
      transform: translateY(-10px) rotateZ(45deg);
    }
</style>