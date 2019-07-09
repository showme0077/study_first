<template>
  <ul id="navMenu">
    <li
      class="menuList"
      v-for="item in menus"
      :key="item.id"
      @click="movePage(item.path)"
    >{{item.name}}</li>
  </ul>
</template>

<script>
export default {
  props: {
    menus: Array
  },
  name: "Navigation",
  methods: {
    movePage: function(path) {
      this.$emit("goPage", path);
    }
  }
};
</script>

<style lang="sass" scoped>
@import "../assets/scss/menu.scss"
</style>