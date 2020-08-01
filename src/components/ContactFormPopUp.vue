<template>
	<v-div>
		

		<h2>Contact Information</h2>
		
		<ul>
		<li>
		<v-text-field
            v-model="name"
            label="Name"
        ></v-text-field>
        </li>
        <li>
        <v-text-field
            v-model="email"
            label="Cpp Email"
        ></v-text-field>
        </li>
        <li>
        <v-text-field
            v-model="major"
            label="Major"
        ></v-text-field>
        </li>
        <li>
        <v-text-field
            v-model="graduationTerm"
            label="Graduation Term"
        ></v-text-field>
        </li>
        <li>  
        <v-textarea
        autocomplete="experience"
        label="Areas of experience (optional)"
      ></v-textarea>
    </li>
        </ul>

        <v-btn medium class="button">Submit</v-btn>



	</v-div>
</template>



<script>
	export default 
	{
		name: "ContactFormPopUp",
		data: () => 
		({

		}),

		props: 
		{	
			popUpTxt: String,
		},
		methods:
		{
			closePopUp: function() {
				this.popUpTxt = "none"
			}
		},
	};
</script>


<style>


.darkbackground{
	width: 100%;
	height: 100%;
	position: absolute;
	background-color: rgba(0,0,0,0.7);

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
h2{
	width: 100%;
	height: 40px;
	margin-top: 40px;
}
ul{
	display: inline-block;
	width:90%;
	padding-right: 25px;
	list-style: none;
}

.contactbtn{
	position: absolute;
	background-color: #F7F7F7;

}
</style>  
