<template>
    <fieldset>
        <!--<slot name="memberTitle"/>-->
        <!--<slot name="idInput"/>-->
        <legend>회원가입</legend>
        <label for="id">id</label>
        <input id="id" type="text" placeholder="id 입력" :readonly="naming === 'update'"/>
        <label for="pw">password</label>
        <input id="pw" type="password" placeholder="password"/>
    </fieldset>
</template>

<script>
    export default {
        name: "SignUp",
        props: {
          naming: {key: String}
        },
        data() {
            return {
                signUpText: {title: "sign-up", desc: "sign-up form", submit: "JOIN"},
                updateText: {}
            }
        },
        mounted() {
            this.$emit('sendText', this.signUpText)
        }
    }
</script>