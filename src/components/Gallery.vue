<template>
    <div class="galleryWrap">
        <div>
            <ul>
                <li v-for="(item, key) in buttons" :key="key">
                    <button v-text="item.name" @click="selected = item.name"></button>
                </li>
            </ul>
        </div>
        <ul class="gallery">
            <li  v-for="(item, key) in images" :key="key">
                {{filterName}}
                <img :src="filterName" alt="">
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
                selected: '',
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
                ]
            }
        },
        methods: {
            // nameFilter: function(button){
            //     return this.images.filter(function (number) {
            //         console.log(number.name)
            //         if(button === number.name)
            //         {
            //             return number.name
            //         }
            //
            //     })
            // }
        },
        computed: {
            filterName: function() {
                let itemUrl = []
                for(let item in this.images ){
                    if(this.selected === item.name){
                        itemUrl.push(item.url)
                        return itemUrl
                    }
                    return itemUrl
                }
            }
        }
    }
</script>

<style scoped>

</style>