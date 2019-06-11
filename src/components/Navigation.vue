<template>
    <ul id="navMenu">
        <li class="menuList" v-for="item in menuItems" v-bind:key="item.key" v-on:click="movePage(item.path)">{{item.name}}</li>
    </ul>
</template>

<script>
export default {
  name: "Navigation",
  data: function(){
    return {
      menuItems: [{key: 0, name: "Home", path:"/"}, {key: 1, name: "Sign Up", path: "signup"}, {key: 2, name: "User Info", path: "userinfo"}]
    }
  },
  methods: {
    movePage: function(path){
      this.$root.$children[0].currentComponent = path
    }
  }
};
</script>

<style lang="sass" scoped>
@import "../assets/scss/menu.scss"
</style>