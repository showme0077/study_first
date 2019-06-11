<template>
  <div id="app">
    <h1>VUE STUDY FIRST</h1>
    <Navigation />
    <SignUp v-if="currentComponent==='signup'" />
    <UserInfo v-if="currentComponent==='userinfo'" />
  </div>
</template>

<script>
import Navigation from "./components/Navigation.vue";
import SignUp from "./components/Sign-up.vue";
import UserInfo from "./components/User-info.vue";

export default {
  name: "app",
  components: {
    Navigation,
    SignUp,
    UserInfo
  },
  data: function(){
    return {
      home: true,
      signUp: false,
      userInfo: false,
      currentComponent: ''
    }
  }
};
</script>

<style>
  #app {
    font-family: "Avenir", Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>