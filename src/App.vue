<template>
  <div id="app">
    <img src="./assets/logo.png" alt="">
    <h1>VUE STUDY FIRST</h1>
    <Navigation />
    <Gallery />
  </div>
</template>

<script>
import Gallery from "./components/Gallery.vue";
import Navigation from "./components/Navigation.vue";

export default {
  name: "app",
  components: {
    Gallery,
    Navigation
  },
  data() {
    return {
    };
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
