<template>
    <AddUpdate :textList="formText" @sendText="receiveText">
        <legend slot="memberTitle">{{formText.title}}</legend>
        <input type="text" placeholder="id를 입력하세요" slot="idInput"/>
    </AddUpdate>
</template>

<script>
import AddUpdate from "./AddUpdate"
export default {
    name: "MembersForm",
    components: {
        AddUpdate
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
