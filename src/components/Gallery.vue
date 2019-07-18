<template>
  <div class="galleryWrap">
    <div>
      <ul>
        <li v-for="(btn, key) in buttons" :key="key">
          <button v-text="btn.name" @click="selected = btn.name"></button>
        </li>
      </ul>
    </div>
        <transition-group tag="ul" class="gallery" name="gallery" >
            <li v-for="item in filterName" :key="item">
              <img :src="item.url" alt>
              <p v-text="item.name"></p>
            </li>
        </transition-group>
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
.gallery li { width: calc(20% - 15px); display: inline-block; margin-left: 10px;}
.gallery li:last-child { margin-right: 10px;}
img {width: 100%;}

.list-enter-active,
.list-leave-active,
.list-move {
transition: 500ms cubic-bezier(0.59, 0.12, 0.34, 0.95);
transition-property: opacity, transform;
}

.list-enter {
opacity: 0;
transform: translateX(50px) scaleY(0.5);
}

.list-enter-to {
opacity: 1;
transform: translateX(0) scaleY(1);
}

.list-leave-active {
position: absolute;
}

.list-leave-to {
opacity: 0;
transform: scaleY(0);
transform-origin: center top;
}


.gallery-enter-active{
    animation: flash 1s;
}
.gallery-leave-active {
    animation: bounceOut 1s;
}
.gallery-enter,
.gallery-leave-to{
  transform: translateX(10px);
  opacity: 0;
}
</style>