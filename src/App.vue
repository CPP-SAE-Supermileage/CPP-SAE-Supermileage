<template>
<!-- IMPORTANT: Each section in the webpage with a menu button requires one element associated with that section be assigned an id -->
<!-- This is so the menu button knows where to scroll to                                                                           -->
<!-- Please follow the conventions below for id names (idAbout, idCompetitions, etc.)                                              -->

  <v-app>

    <Menu/>
  
    <v-main> 

		<Slideshow /> 
		<About id="idAbout"/>

		
		<Competitions id="idCompetitions"/>
        <ImageDisplayer id="idMembers" :imgSrc="'members.png'" :displayHeight="400" headerTxt="Join the Team!"/>
		<Members/>
		<ImageDisplayer id="idSponsors" :imgSrc="'sponsors.png'" :displayHeight="400" headerTxt="Sponsors" txt="None of this would be possible without our sponsors!"/>
		<Sponsors/>

		<ImageDisplayer id="idDonate" :imgSrc="'donate.png'" :displayHeight="200" headerTxt="Donate to CPP SAE Supermileage"/>
		<Donate/>

		<Contact id="idContact"/>
        <Form id="idContactForm" style="display: none;"/>
    </v-main>
  </v-app>
</template>

<script>
	import Menu           from './components/Menu';
	import Slideshow      from './components/Slideshow';
	import About          from './components/About';
	import Competitions   from './components/Competitions';
	import Donate         from './components/Donate';
	import Contact        from './components/Contact';
	import ImageDisplayer from './components/ImageDisplayer';

	import Sponsors		  from './components/Sponsors';
    import Members        from './components/Members';
	import Form           from './components/Form';

	export default 
	{
		name: 'App',
        
		components: 
		{
			Menu,
			Slideshow,
			About,
			Competitions,
			Donate,
			Contact,
			ImageDisplayer,

			Sponsors,
            Members,
			Form,
		},
	};
</script>

<style>
    p
    {
        text-align: center;
        padding-left: 10vw;
        padding-right: 10vw;
    }
    h2
    {    text-align: center;}
</style>