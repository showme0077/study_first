<template>
    <div class="wrap">
        <div id="example-3">
            <button @click="show = !show">
                Toggle render
            </button>
            <transition
                    name="custom-classes-transition"
                    enter-active-class="animated tada"
                    leave-active-class="animated bounceOutRight"
            >
                <p v-if="show">hello</p>
            </transition>
        </div>


        <div class="timerWrap">
            <label for="timer">Timer 설정</label>
            <input id="timer" type="number" v-model="timer" placeholder="숫자만 입력하세요."/>
            <button id="timerSubmit" @click="startRotation">확인</button>
        </div>
        <div class="contentsWrap">
        <transition
            name="slide-transition"
            enter-active-class="animated tada"
            leave-active-class="animated bounceOutRight"
        >
            <p> {{slideText[currentNumber]}} </p>
        </transition>
        <button v-text="slideStatus" @click="autoPlay"></button>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Slide",
        data() {
            return {
                slideText: ["ONE", "TWO", "THREE", "FOUR"],
                currentNumber: 0,
                timer: 0,
                slideStatus: "play",
                autoplay: null,
                show: true
            }
        },
        methods: {
            autoPlay: function(){
                if(this.slideStatus === 'play' && this.timer !== 0){
                    this.startRotation()
                    this.slideStatus = "stop"
                }else if(this.slideStatus === 'stop' && this.timer !== 0) {
                    this.stopRotation()
                    this.slideStatus = "play"
                }else {
                    alert('Timer 설정해주세요')
                }
            },
            startRotation: function() {
                this.autoplay = setInterval(this.next, this.timer*1000);
            },
            stopRotation: function() {
                clearTimeout(this.autoplay);
                this.autoplay = null
            },

            next: function() {
                this.currentNumber += 1
            },
            prev: function() {
                this.currentNumber -= 1
            }
        }
    }
</script>

<style scoped>

</style>