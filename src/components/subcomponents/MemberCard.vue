<template>
<!-- ONLY FOR USE IN Members.vue                                                       -->
<!-- If you need to add a new Membercard to the Members section, add it in Members.vue -->
<v-card class="testcardclass" elevation="1" outlined tile width="350" max-height="500">

    <v-row justify="center">
        <v-avatar  color="indigo" size="200">
            <v-img v-if="imageName" alt="Member Profile Picture" :src="require('@/assets/members/' + imageName)"/>
            <span v-else class="white--text">{{name.charAt(0) + name.substring(name.indexOf(' ')).charAt(1)}}</span>
        </v-avatar>
    </v-row>
        
    <v-card-title class="memberCardTitle">{{titleText}}</v-card-title>  
    <v-card-subtitle  class="memberCardSubtitle">{{subtitleText}}</v-card-subtitle>
    
    <v-card-text>
    <v-row>
        <v-img   v-if="email"   height='40' width='40' @mouseover="showInfo(0)" @mouseout="hideInfo()" alt="Email Icon"    contain @click="copyText(0)"  :src="require('@/assets/members/EmailIcon.png')"/>
        <v-img   v-if="github"  height='40' width='40' @mouseover="showInfo(2)" @mouseout="hideInfo()" alt="Github Link"   contain @click="openInNewTab('https://www.github.com/' + github)"  :src="require('@/assets/members/GithubIcon.png')" />
        <v-img   v-if="discord" height='40' width='40' @mouseover="showInfo(1)" @mouseout="hideInfo()" alt="Discord Icon"  contain @click="copyText(1)"  :src="require('@/assets/members/DiscordIcon.png')" />
       
    </v-row>
    </v-card-text>

</v-card>    
</template>

<script>
    export default
    {
        name: "MemberCard",
        
        props:
        {
            name:      String,
            roles:     String,
            email:     String,
            discord:   String,
            github:    String,
            imageName: String,
        },
        
        methods:
        {
            openInNewTab(url) 
            {
                const win = window.open(url, '_blank');
                win.focus();
            },
            
            copyText(buttonCode)
            {
                var text;
                switch(buttonCode)
                {
                    case 0:
                        text = this.email;
                        break;
                    case 1:
                        text = this.discord;
                        break;
                }
                navigator.clipboard.writeText(text);
                
            },
            
            showInfo(buttonCode)
            {
                switch(buttonCode)
                {
                    case 0:
                        this.titleText    = this.email;
                        this.subtitleText = "Click to copy email address."
                        break;
                    case 1:
                        this.titleText    = this.discord;
                        this.subtitleText = "Click to copy Discord username."
                        break;
                    case 2:
                        this.titleText =    this.github;
                        this.subtitleText = "Click to visit Github.";
                        break;
                }
                document.body.style.cursor = 'pointer';
            },
            
            hideInfo()
            {
                this.titleText = this.name;
                this.subtitleText = this.roles;
                document.body.style.cursor = 'auto';
            }
        },

        mounted()
        {
            this.titleText = this.name;
            this.subtitleText = this.roles;
        },
        
        data: () =>
        ({
            titleText: '',
            subtitleText: '',
        }),
    };
</script>

<style scoped>
    .memberCardTitle
    {
        font-size: 1.4em;
    }
    .memberCardSubtitle
    {
        font-size: 1.1em;
    }
    span
    {
        font-size: 3.2em
    }
</style>