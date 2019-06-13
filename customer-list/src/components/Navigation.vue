<template>
    <nav>
        <div class="nav-wrapper">
            <ul id="nav-mobile" class="right hide-on-med-and-down">
                <li><a href="#" @click="clickMenu(true)">sign up</a></li>
                <li><a href="#" @click="clickMenu(false)">customer list</a></li>
            </ul>
        </div>
    </nav>
</template>

<script>
  export default {
    name: "Navigation",
    methods:{
      clickMenu(flag){
        this.$emit('navResult', flag)
      }
    }
  }
</script>

<style scoped>

</style>
