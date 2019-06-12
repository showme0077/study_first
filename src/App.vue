<template>
  <div id="app">
    <h1>VUE STUDY FIRST</h1>
    <Navigation @goPage="test"/>
    <SignUp v-if="currentComponent==='signup'" @popupOn="onPopup= true"/>
    <UserInfo v-if="currentComponent==='userinfo'"/>
    <Popup v-if="onPopup === true" @closePopup="onPopup=false"/>
  </div>
</template>

<script>
import Navigation from "./components/Navigation.vue";
import SignUp from "./components/Sign-up.vue";
import UserInfo from "./components/User-info.vue";
import Popup from "./components/Popup.vue";

export default {
  name: "app",
  components: {
    Navigation,
    SignUp,
    UserInfo,
    Popup
  },
  data: function() {
    return {
      currentComponent: "",
      onPopup: false
    };
  },
  created() {},
  methods: {
    test: function(e) {
      this.currentComponent = e;
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
#app > h1 {
  font-size: 30px;
  font-weight: bold;
  margin-bottom: 20px;
}
</style>

<style lang="sass">
  @import "./assets/scss/common.scss"
</style>
