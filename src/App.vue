<template>
  <div id="app">
    <img src="./assets/logo.png" alt="">
    <h1>VUE STUDY FIRST</h1>
    <Navigation :menus="menuItems" @goPage="pageMove"/>
    <Gallery v-if="currentPage ==='gallery'"/>
    <AddUpdate v-if="currentPage=== 'update' || currentPage=== 'sign-up'" :naming="currentPage"/>
    <Slide v-if="currentPage === 'slide'"/>
  </div>
</template>

<script>
import Navigation from "./components/Navigation.vue"
import Gallery from "./components/Gallery.vue"
import AddUpdate from "./components/AddUpdate.vue"
import Slide from "./components/Slide.vue"


export default {
  name: "app",
  components: {
    Navigation,
    Gallery,
    AddUpdate,
    Slide
  },
  data() {
    return {
      menuItems: [
        { key: 0, name: "Home", path: "/" },
        { key: 1, name: "Gallery", path: "gallery" },
        { key: 2, name: "sign-up", path: "sign-up" },
        { key: 3, name: "update", path: "update" },
        { key: 4, name: "slide", path:"slide"}
      ],
      currentPage: ''
    }
  },
  methods: {
    pageMove: function(e){
      this.currentPage = e
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

<style>
  @import "https://cdn.jsdelivr.net/npm/animate.css@3.5.1";
  @import "./assets/scss/common.scss";
</style>
