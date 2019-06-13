<template>
    <table>
        <caption>유저 정보</caption>
        <thead>
            <tr>
                <th>이름</th>
                <th>나이</th>
                <th></th>
            </tr>
        </thead>
    </table>
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
    created: function () {
        EventBus.$on("userInfo", user => {
            this.currentUser = user;
            console.log(this.currentUser)
        })
    }
}
</script>