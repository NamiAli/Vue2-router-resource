<template>
	<div class="test">
		<input  type='text' v-model='title' /> <br />
		<h1>{{title}}</h1>
		<p v-if='showName'>{{user.firstName}}</p>
		<p v-else='showName'>Nobody</p>
		<ul>
			<li v-for='item in items'>{{item.title}}</li>
		</ul>
		<button v-on:click='message'>Message</button>
		<br/>
		<input type='text' v-on:keyup='keypress' v-on:keyup.enter='enterHit'/>
        <hr />
        <label>First Name: </label><input type='text' v-model='user.firstName' />
        <br/>
        <label>Last Name: </label><input type='text' v-model='user.lastName' />
        <h3>{{fullName}}</h3>
        <h2>{{msg}}</h2>
	</div>
</template>



<script>
   
    export default {
    	name:'Test',
        props: {
            msg:{
                type: String,
                default: 'foobar'
            }
        },
    	data(){
    		return{
    			title: 'Hello World',
    			user:{
    				firstName:'Nami',
    				lastName:'Khan'

    			},

    			showName:false,

    			items: [
    			   {title: 'item one'},
    			   {title: 'item two'},
    			   {title: 'item three'}
    			]
    		}
    	},

    	methods:{
    		message:()=>{
    			alert("Hello")
    		},

    		keypress: (e) => {
    			console.log(e.target.value)
    		},

            enterHit: () => {
                console.log('you hit enter')
            }
    	},

        computed: {
            fullName: function(){
                return this.user.firstName + ' ' + this.user.lastName;
            }
        }

    }
 
</script>



<style scoped>
 
</style>