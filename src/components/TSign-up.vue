<template>
  <form action="#">
    <fieldset>
      <legend>회원 가입 양식</legend>
      <div class="box">
        <label for="name">Name</label>
        <input
          id="name"
          type="text"
          placeholder="이름을 입력하세요"
          v-model="newUserModel.newName"
          :class="{'errorInput': validationCheck}"
        >
        <p class="errorValidation" v-if="newUserModel.newName==''">값을 입력해주세요.</p>
      </div>
      <div class="box">
        <label for="age">Age</label>
        <input
          id="age"
          type="text"
          placeholder="나이를 입력하세요"
          v-model="newUserModel.newAge"
          :class="{'errorInput': validationCheck}"
        >
        <p class="errorValidation" v-if="newUserModel.newAge==''">값을 입력해주세요.</p>
      </div>
      <div class="box" >
        <label for="phone">Phone</label>
        <input
          id="phone"
          type="text"
          placeholder="전화번호를 입력하세요"
          v-model="newUserModel.newPhone"
          :class="{'errorInput': validationCheck}"
        >
        <p class="errorValidation" v-if="newUserModel.newPhone==''">값을 입력해주세요.</p>
      </div>
      <div class="box">
        <label for="address">Address</label>
        <input
          id="address"
          type="text"
          placeholder="주소를 입력하세요"
          v-model="newUserModel.newAddress"
          :class="{'errorInput': validationCheck}"
        >
        <p class="errorValidation" v-if="newUserModel.newAddress==''">값을 입력해주세요.</p>
      </div>

      <input @click="addUser" type="submit" value="회원 가입">
    </fieldset>
  </form>
</template>

<script>
import { EventBus } from "../main.js";
export default {
  name: "SignUp",
  created() {
    EventBus.$emit("userInfo", this.user);
  },
  data: function() {
    return {
      newUserModel: {
        newName: "",
        newAge: "",
        newPhone: "",
        newAddress: ""
      },
      user: [
        {
          key: 1,
          userName: "yoo",
          userAge: "20",
          userNumber: "010-4203-5294",
          userAddress: "서울"
        },
        {
          key: 2,
          userName: "kim",
          userAge: "30",
          userNumber: "010-1111-0000",
          userAddress: "대전"
        },
        {
          key: 3,
          userName: "lee",
          userAge: "43",
          userNumber: "010-1123-3222",
          userAddress: "대구"
        },
        {
          key: 4,
          userName: "park",
          userAge: "34",
          userNumber: "010-3523-1029",
          userAddress: "부산"
        }
      ]
    };
  },
  methods: {
    validationCheck() {

    },
    addUser: function() {
      if (
        this.newName !== "" &&
        this.newAge !== "" &&
        this.newPhone !== "" &&
        this.newAddress !== ""
      ) {
        this.user.push({
          key: this.user.length,
          userName: this.newName,
          userAge: this.newAge,
          userNumber: this.newPhone,
          userAddress: this.newAddress
        });
        this.newName = "";
        this.newAge = "";
        this.newPhone = "";
        this.newAddress = "";
        this.$emit("popupOn");
        EventBus.$emit("userInfo", this.user);
      }
    }
  }
};
</script>

<style lang="sass" scoped>
@import "../assets/scss/signUp.scss"
</style>