<<template>
	<div class='users'>
		<h1>Users</h1>

		<input type='text' v-model="newUser.user" placeholder="Enter name" /> <br />
		<input type='text' v-model="newUser.email" placeholder="Enter email" /> <br />
		<input type='submit' value='Submit' v-on:click='add'/>
		<ul>
			<li v-for='user in users'>
            <input type='checkbox' class='toggle' v-model='user.contacted'/>
            <span :class="{contacted:user.contacted}">
            	{{user.name}}: {{user.email}} 
            	<button v-on:click='deleteUser(user)'>x</button>
            </span>
			</li>
		</ul>

		
	</div>
</template>


<script>
	
   export default {

   	    data(){

   	    	return {

   	    		 newUser:{},

   	    		  users:[]  
   	    	}
   	    },

   	    methods: {

   	    	 add: function(){
   	    	 	this.users.push({
   	    	 		user: this.newUser.user,
   	    	 		email: this.newUser.email,
   	    	 		contacted: false
   	    	 	})
   	    	 },
   	    	 deleteUser: function(user){
                 this.users.splice(this.users.indexOf(user), 1)
   	    	 }
   	    },

        created: function(){
          this.$http.get('https://jsonplaceholder.typicode.com/users').then(function(response){
               this.users = response.data;
          });
        }




   }



</script>

<style scoped>
	.contacted{
		text-decoration: line-through;
	}
</style>