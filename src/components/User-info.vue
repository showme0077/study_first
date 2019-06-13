<template>
    <span>User-info</span>
</template>

<script>
import { EventBus } from "../main.js"
export default {
    name: "User-info",
    data: function(){
        return {
            currentUser: {}
        }
    },
    created(){
        EventBus.$on("userInfo", user => {
            this.currentUser = user;
            console.log(this.currentUser)
        })
    }
}
</script>