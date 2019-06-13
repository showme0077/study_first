<template>
    <div class="row">
        <form class="col s12">
            <div class="row">
                <div class="input-field col s6">
                    <input placeholder="Username" @keyup="resetValidation('name')" id="userName" type="text" class="validate" v-model="userName">
                    <label for="userName"></label>
                    <span v-if="this.validation.name.active">{{this.validation.name.message}}</span>
                </div>
                <div class="input-field col s6">
                    <input paceholder="" id="userAge" @keyup="resetValidation('age')" type="number" min="0" class="validate" v-model="userAge">
                    <label for="userAge">Age</label>
                    <span v-if="this.validation.age.active">{{this.validation.age.message}}</span>
                </div>
            </div>
            <div class="row">
                <div class="input-field col s12">
                    <input id="phoneNumber" type="text" @keyup="resetValidation('phone')" class="validate" v-model="phoneNumber">
                    <label for="phoneNumber">phoneNumber</label>
                    <span v-if="this.validation.phone.active">{{this.validation.phone.message}}</span>
                </div>
            </div>
            <div class="row">
                <div class="input-field col s12">
                    <input id="userAddress" type="text" @keyup="resetValidation('addr')" class="validate" v-model="userAddress">
                    <label for="userAddress">userAddress</label>
                    <span v-if="this.validation.addr.active">{{this.validation.addr.message}}</span>
                </div>
            </div>
        </form>
        <div>
            <a class="waves-effect waves-light btn" @click="resetData">초기화</a>
            <a class="waves-effect waves-light btn" @click="saveUser">저장</a>
        </div>
    </div>
</template>

<script>
  const province = ['서울' ,'대전', '대구', '부산']
  export default {
    name: "Sign-up",
    data(){
      return {
        userName : '',
        userAge : '',
        phoneNumber : '',
        userAddress: '',
        validation: {
          name : {
            active: false,
            message: ''
          },
          age : {
            active: false,
            message: ''
          },
          phone : {
            active: false,
            message: ''
          },
          addr : {
            active: false,
            message: ''
          },
        }
      }
    },
    methods: {
        saveUser(){
          if(this.userName.length < 1) {
            this.validation.name.active = true
            this.validation.name.message = '이름을 입력하세요'
            return
          }
          if(this.userAge.length < 1) {
            this.validation.age.active = true
            this.validation.age.message = '나이를 입력하세요'
            return
          }
          if(this.phoneNumber.length < 1) {
            this.validation.phone.active = true
            this.validation.phone.message = '전화번호를 입력하세요'
            return
          }
          if(this.userAddress.length < 1) {
            this.validation.addr.active = true
            this.validation.addr.message = '주소를 입력하세요'
            return
          }
          let flag = false
          province.map(prov=>{
            if(prov === this.userAddress) flag = true
          })
          if(flag) {
            const saveData = {
              userName : this.userName,
              userAge : this.userAge,
              phoneNumber : this.phoneNumber,
              userAddress: this.userAddress
            }
            this.$emit('saveData', saveData)
            alert("회원가입이 완료되었습니다.")
            this.resetData()
          }else {
            this.validation.addr.active = true
            this.validation.addr.message = '유효한 지역을 입력하세요'
            return
          }
        },
        resetData(){
          this.userName = ''
          this.userAge = ''
          this.phoneNumber = ''
          this.userAddress = ''
        },
        resetValidation(index){
          this.validation[index].active = false
        }
    }
  }
</script>

<style scoped>

</style>
