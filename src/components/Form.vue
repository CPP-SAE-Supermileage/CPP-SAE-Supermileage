<template>
<v-form ref="form" v-model="valid" lazy-validation>
	<ul>
	<li>
	<v-text-field 
        v-model="name"
        :rules="nameRules"
        label="Name"

        required
      ></v-text-field>
	</li>
    <li>
      <v-text-field
        v-model="email"
        :rules="emailRules"
        label="E-mail"
        required
      ></v-text-field>
    </li>
    <li>
      <v-text-field
        v-model="major"
        :rules="majorRules"
        label="Major"
        required
      ></v-text-field>
    </li>
    <li>
      <v-text-field
        v-model="gradTerm"
        :rules="gradRules"
        label="Graduation Term"
        required
      ></v-text-field>
    </li>
    
    <v-row>
    <h6 style="margin-left:1em; margin-top:1em; color:#686868;">Areas of interest: </h6>
    </v-row>

    <v-row>
    <v-col cols="12"  sm="6">
        <v-row>
        <h6 style="margin-left:1em; color:#686868;">Computer Science</h6>
        </v-row>
    <v-checkbox style="margin:0;"
        label="ML/CV"
        hide-details
    ></v-checkbox>
    <v-checkbox
        label="CoppoliaSIM"
        hide-details
    ></v-checkbox>
    <v-checkbox
        label="Hardware"
        hide-details
    ></v-checkbox>
    </v-col>
    <v-col cols="12"  sm="6">
    <v-row>
        <h6 style="margin-left:1em; color:#686868;">Engineering</h6>
        </v-row>
    <v-checkbox style="margin:0;"
        label="CFD"
        hide-details
    ></v-checkbox>
    <v-checkbox
        label="Design"
        hide-details
    ></v-checkbox>
    <v-checkbox
        label="Electrical"
        hide-details
    ></v-checkbox>
    </v-col>
    </v-row>

    <v-textarea
    outlined
        name="experienceText"
        label="Areas of experience (optional)"
        ></v-textarea>

        <v-btn>
        Submit
        </v-btn>
    </ul>

</v-form>
</template>



<script>
export default 
{
    name: "",
    data: () =>
    ({
        valid: true,
        name: '',
        nameRules: [
            v => !!v || 'Name is required', ],
        email: '',
        emailRules: [
            v => !!v || 'E-mail is required',
            v => /.+@.+\..+/.test(v) || 'E-mail must be valid', ],
        major: '',
        majorRules: [
            v => !!v || 'Major is required', ],
        gradTerm: '',
        gradRules: [
            v => !!v || 'Graeduation term is required', ],
    }),
 }
</script>


<style>
li{
	height:65px;
	list-style:none;
}
ul{
    padding:0;
    margin:0;
}
.v-text-field{
    position: absolute;
    width:90%;
}
</style>  
