<template>
  <div id="app">
    <img src="./assets/logo.png" alt="">
    <h1>VUE STUDY FIRST</h1>
    <Navigation />
    <p>{{total}}</p>
    <Study v-on:increment="incrementTotal" />
    <Study v-on:increment="incrementTotal" />
  </div>
</template>

<script>
import Navigation from "./components/Navigation.vue";
import Study from "./components/Study.vue";

export default {
  name: "app",
  components: {
    Navigation,
    Study
  },
  data() {
    return {
      total: 0
    }
  },
  methods: {
    incrementTotal: function() {
      this.total += 1
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
