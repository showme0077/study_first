<template>
  <div id="app">
    <img src="./assets/logo.png" alt="">
    <h1>VUE STUDY FIRST</h1>
    <Navigation :menus="menuItems" @goPage="pageMove"/>
    <Gallery v-if="currentPage ==='gallery'"/>
    <Member-form v-if="currentPage==='member-form'"/>
  </div>
</template>

<script>
import Navigation from "./components/Navigation.vue"
import Gallery from "./components/Gallery.vue"
import MemberForm from "./components/MemberForm.vue"

export default {
  name: "app",
  components: {
    Navigation,
    Gallery,
    MemberForm
  },
  data() {
    return {
      menuItems: [
        { key: 0, name: "Home", path: "/" },
        { key: 1, name: "Gallery", path: "gallery" },
        { key: 2, name: "Study", path: "member-form" }
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

<style lang="sass">
  @import "./assets/scss/common.scss"
</style>
