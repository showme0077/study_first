<template>
    <div class="galleryWrap">
        <div v-if="images">
            <ul>
                <li v-for="(item, key) in buttons" :key="key">
                    <button v-text="item.name" @click="nameFilter(item.name)"></button>
                </li>
            </ul>
        </div>
        <ul class="gallery">
            <li  v-for="(item, key) in images" :key="key" >
                <img :src="item.url" alt="">
                <p v-text="item.name"></p>
            </li>
        </ul>
    </div>
</template>

<script>
    export default {
        name: "gallery",
        data() {
            return {
                buttons: [
                    {id: 0, name: "all"},
                    {id: 1, name: "hodu"},
                    {id: 2, name: "jadu"},
                    {id: 3, name: "hodujadu"}
                ],
                images: [
                    {id: 0, name: "hodu", url: require('@/assets/images/hodu1.png')},
                    {id: 1, name: "hodujadu", url: require('@/assets/images/hodujadu1.png')},
                    {id: 2, name: "jadu", url: require("@/assets/images/jadu1.png")},
                    {id: 3, name: "jadu", url: require("@/assets/images/jadu2.png")},
                    {id: 4, name: "jadu", url: require("@/assets/images/jadu3.png")}
                ],
                numbers: [ 'a', 'b', 'c', 'd', '5' ]
            }
        },
        methods: {
            nameFilter: function(name){
                return this.images.filter(function (number) {
                    console.log(number.name === name)
                    return number.name  === name
                })
            }
        },
        computed: {
            evenNumbers: function (name) {
                return this.images.filter(function (number) {
                    console.log(number)
                    return number.name  === name
                })
            }
        }
    }
</script>

<style scoped>

</style>