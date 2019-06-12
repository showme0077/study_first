<template>
  <div class="dimmed">
    <div class="popupWrap">
      <div class="content">
        <strong>가입이 완료되었습니다.</strong>
        <button @click="confirm">확인</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Popup",
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

