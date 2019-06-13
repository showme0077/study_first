<template>
  <div id="app" class="container">
    <Navigation @navResult="clickMenu"></Navigation>

    <SignUp @saveData="addNewUser" v-if="router"></SignUp>
    <CustomerList :list="userList" v-if="!router" @deleteUser="removeUser"></CustomerList>
    <span class="toast" v-if="toastFlag">추가되었습니다.</span>
  </div>
</template>

<script>
import Navigation from './components/Navigation.vue'
import SignUp from './components/Sign-up.vue'
import CustomerList from'./components/Customer-list'
export default {
  name: 'app',
  components: {
    SignUp,
    Navigation,
    CustomerList
  },
  data() {
    return {
      userList : [],
      router : true,
      toastFlag: false
    }
  },
  methods: {
    addNewUser(data){
      this.userList.push(data)
      this.toastFlag = true
      setTimeout(()=>{
        this.toastFlag = false
      },2000)
    },
    clickMenu(flag){
      this.router = flag
    },
    removeUser(userId){

      if(confirm(`${userId}를 삭제하시겠습니까?`)) {
        let index;
        this.userList.map((user,i)=>{
          if(user.userName===userId) index = i
        })
        this.userList.splice(index, 1)
      }

    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
  .toast {
    background-color: #2c3e50;
  }
</style>
