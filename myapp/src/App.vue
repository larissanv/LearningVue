<template>
  <div id="app">
    <img src="./assets/logo.png">
    <!-- <router-view/> -->
    <!-- <home msg="Override"></home> -->
    <users></users>
  </div>
</template>

<script>
import Home from './components/home';
import Users from './components/users';

export default {
  name: 'App',
  components: {
    Home, Users
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
