<template>
  <div id="app">
    <h1>VUE STUDY FIRST</h1>
    <Navigation />
    <SignUp @current="test" v-if="currentComponent==='signup'" />
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
  props: {
    currentComponent: String
  },
  data: function(){
    return {
      home: true,
      signUp: false,
      userInfo: false,
      // currentComponent: ''
    }
  },
  methods: {
    test(path){
      this.currentComponent = path
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