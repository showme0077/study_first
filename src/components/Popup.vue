<template>
  <div class="dimmed">
    <div class="popupWrap">
      <div class="content">
        <slot name="pTag"/>
        <strong>{{popupText.desc}}</strong>
        <slot name="input"/>
        <slot/>
        <button @click="confirm">확인</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Popup",
  props: ["popupText"],
  methods: {
    confirm: function() {
      this.$emit("closePopup");
    }
  }
};
</script>

<style lang="sass" scoped>
@import "../assets/scss/popup.scss"
</style>

