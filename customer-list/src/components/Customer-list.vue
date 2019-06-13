<template>
    <div>
    <table>
        <thead>
        <tr>
            <th>이름</th>
            <th>나이</th>
            <th>전화번호</th>
            <th>지역</th>
            <th></th>
        </tr>
        </thead>
        <tbody>
        <tr v-for="user in list" :user="user" :key="user.userName">
            <td>{{user.userName}}</td>
            <td>{{user.userAge}}</td>
            <td>{{user.phoneNumber}}</td>
            <td>{{user.userAddress}}</td>
            <td><button @click="removeUser(user.userName)">삭제</button></td>
        </tr>
        </tbody>
    </table>
</div>
</template>

<script>
  export default {
    name: "Customer-list",
    props: ['list'],
    methods: {
      removeUser(userId){
        this.$emit('deleteUser', userId)
      }
    }
  }
</script>

<style scoped>

</style>
