<template>
    <SignUp :textList="formText" @sendText="receiveText">
        <legend slot="memberTitle">{{formText.title}}</legend>
        <input type="text" placeholder="id를 입력하세요" slot="idInput"/>
    </SignUp>
</template>

<script>
import SignUp from "../components/SignUp"
export default {
    name: "MembersForm",
    components: {
      SignUp
    },
    data() {
        return {
            formText: {
                title: "",
                desc: "",
                submit: ""
            }
        }
    },
    methods: {
        receiveText(t) {
            this.formText.title = t.title
            this.formText.desc = t.desc
            this.formText.submit = t.submit
        }
    }
};
</script>
