<template>
  <div class="galleryWrap">
    <div>
      <ul>
        <li v-for="(btn, key) in buttons" :key="key">
          <button v-text="btn.name" @click="selected = btn.name"></button>
        </li>
      </ul>
    </div>
    <ul class="gallery">
      <li v-for="(item, key) in filterName" :key="key">
        <img :src="item.url" alt>
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
      selected: "",
      itemUrl: [],
      buttons: [
        { id: 0, name: "all" },
        { id: 1, name: "hodu" },
        { id: 2, name: "jadu" },
        { id: 3, name: "hodujadu" }
      ],
      images: [
        { id: 0, name: "hodu", url: require("@/assets/images/hodu1.png") },
        {
          id: 1,
          name: "hodujadu",
          url: require("@/assets/images/hodujadu1.png")
        },
        { id: 2, name: "jadu", url: require("@/assets/images/jadu1.png") },
        { id: 3, name: "jadu", url: require("@/assets/images/jadu2.png") },
        { id: 4, name: "jadu", url: require("@/assets/images/jadu3.png") }
      ]
    };
  },
  methods: {},
  computed: {
    filterName() {
      let newArr = [];
      /*
                // map
                this.images.map(image => {
                    if(image.name === this.selected) {
                        newArr.push(image)
                    }
                })
                */

      //reduce
      this.images.reduce((index, image) => {
        if (this.selected === image.name) {
          newArr.push(image);
        } else if (this.selected === "all") {
          newArr.push(image);
        }
      }, 0);

      /*
                //for of
                for(let item of this.images){
                    if(item.name === this.selected) {
                        newArr.push(item)
                    }
                }
                */
      return newArr;
    }
  }
};
</script>

<style scoped>
</style>