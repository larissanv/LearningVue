<template>
    <div class="home">
        <input type="text" v-model="title"><br/>
        <span v-html="title"></span>
        <p v-if="showName">{{user.firstName}} {{user.lastName}}</p>
        <p v-else>Nobody</p>
        <ul>
            <li v-for="item in items">{{item.title}}</li>
        </ul>
        <button v-on:click="greet">Say Greeting</button><br/>
        <input type="text" v-on:keyup="pressKey" v-on:keyup.enter="enterHit">
        <br/>
        <hr/>
        <label>First Name: </label><input type="text" v-model="user.firstName">
        <label>Last Name: </label><input type="text" v-model="user.lastName">
        <h3>{{fullname}}</h3>
        <br/>
        <h2>{{msg}}</h2>
  </div>
</template>
<script>
export default {
    name: 'home',
    props: {
        msg: { 
            type: String,
            default: "foobar"
        }
    },
    data(){
        return{
            title: '<h2>Hello World!</h2>',
            user: {
                firstName: 'Larissa',
                lastName: 'Viana'
            },
            showName: false,
            items: [
                {title: 'Item 1'},
                {title: 'Item 2'},
                {title: 'Item 3'},
            ]
        }
    },
    methods: {
        greet: function(){
            alert('Hello');
        },
        pressKey: function(e){
            console.log(e.target.value);
        },
        enterHit: function(){
            console.log("You hit enter");
        }
    },
    computed:{
        fullname: function(){
            return this.user.firstName + ' ' + this.user.lastName
        }
    }
}
</script>
<style scoped>

</style>


