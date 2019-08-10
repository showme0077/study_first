<template>
    <div class="wrap">
        <div class="timerWrap">
            <label for="timer">Timer 설정</label>
            <input id="timer" type="number" v-model="timer" placeholder="숫자만 입력하세요."/>
            <button id="timerSubmit" @click="startRotation">확인</button>
        </div>
        <div class="addWrap">
            <label for="addText">슬라이드 추가</label>
            <input id="addText" type="text" placeholder="슬라이드에 추가할 내용 입력"/>
            <button id="add">추가</button>
        </div>
        <div class="contentsWrap"
             @mouseover="stopRotation"
             @mouseout="startRotation">
            <a @click="prev">Previous</a> || <a @click="next">Next</a>
            <transition name="fade">
                <p> {{slideText[Math.abs(currentNumber) % slideText.length]}} </p>
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
                addText: "",
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
    .fade-transition {
        transition: all 0.8s ease;
        overflow: hidden;
        visibility: visible;
        opacity: 1;
        position: absolute;
    }
    .fade-enter, .fade-leave {
        opacity: 0;
        visibility: hidden;
    }
</style>