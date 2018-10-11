<template>
    <div class="users">
       <h1>users</h1>
       <form v-on:submit="addUser">
         <input type="text" v-model="newUser.name" placeholder="Enter name">
         <br/>
         <input type="text" v-model="newUser.email" placeholder="Enter email">
         <br />
         <input type="submit">
       </form>
       <ul>
           <li v-for="user in users">
            <input type="checkbox" class="toggle" v-model="user.contacted">
            <span :class="{contacted: user.contacted}">
               {{user.name}}: {{user.email}}
               <button v-on:click="deleteUser">X</button>
            </span>
           </li>
       </ul>
  </div>
</template>
<script>
export default {
    name: 'users',
   
    data(){
        return{
        newUser: {},
        users: []
      }
    },
    methods: {
      deleteUser: function(user){
         this.users.splice(this.users.indexOf(user),1);
       },
       addUser: function(e){
         console.log('add');
         this.users.push({
           name: this.newUser.name,
           email: this.newUser.email,
           contacted: false
         })
         e.preventDefault();
       },
       
    },
    created: function(){
      this.$http.get('https://jsonplaceholder.typicode.com/users')
      .then(function(response){
        this.users =response.data;
      });
    }
}
</script>
<style scoped>
  .contacted{
    text-decoration: line-through;
  }
</style>


