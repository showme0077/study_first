<template>
    <fieldset>
        <slot name="memberTitle"/>
        <slot name="idInput"/>
    </fieldset>
</template>

<script>
    export default {
        name: "SignUp",
        props: {
          textList: Object
        },
        data() {
            return {
                signUpText: {title: "sign-up", desc: "sign-up form", submit: "JOIN"}
            }
        },
        mounted() {
            this.$emit('sendText', this.signUpText)
        }
    }
</script>