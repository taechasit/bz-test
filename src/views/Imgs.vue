<template>
  <div>
    <div class="container">
      <div
        class="imgContainer"
        @click="onOpenImg(index)"
        v-for="(item, index) in data"
        :key="item + '01'"
      >
        <img :src="getImgUrl(item)" :alt="item" />
      </div>
      <div
        class="btnContainer"
        :style="{ visibility: `${openState ? 'visible' : 'hidden'}` }"
      >
        <button @click="prev">prev</button>
        <button @click="next">next</button>
      </div>
      <div
        class="slideContainer"
        :style="{ visibility: `${openState ? 'visible' : 'hidden'}` }"
      >
        <div class="slider">
          <div class="item">
            <img :src="getImgUrl(data[slideState])" alt="item" />
          </div>
        </div>
      </div>
      <div
        class="backDrop"
        @click="onCloseImg"
        :style="{ visibility: `${openState ? 'visible' : 'hidden'}` }"
      ></div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Gallery",
  components: {},
  data() {
    return {
      data: [
        "fruit-01.jpg",
        "fruit-02.jpg",
        "fruit-03.jpg",
        "fruit-04.jpg",
        "fruit-05.jpg",
        "fruit-06.jpg",
        "fruit-07.jpg",
        "fruit-08.jpg",
        "fruit-09.jpg",
        "fruit-10.jpg",
        "fruit-11.jpg",
        "fruit-12.jpg",
      ],
      slideState: 0,
      openState: false,
    };
  },
  mounted() {},
  methods: {
    getImgUrl(pic) {
      return require("../assets/" + pic);
    },
    prev() {
      if (this.slideState === 0)
        return (this.slideState = this.data.length - 1);
      this.slideState -= 1;
    },
    next() {
      if (this.slideState === this.data.length - 1)
        return (this.slideState = 0);
      this.slideState += 1;
    },
    onOpenImg(index) {
      this.slideState = index;
      this.openState = true;
    },
    onCloseImg() {
      this.openState = false;
    },
  },
};
</script>

<style scoped>
.backDrop {
  width: 100%;
  height: 100%;
  position: fixed;
  top: 0;
  background-color: rgba(0, 0, 0, 0.521);
}
.btnContainer {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  display: flex;
  justify-content: space-between;
  z-index: 3;
  width: 876px;
  background-color: transparent;
}
button {
  border: none;
  border-radius: 20px;
  padding: 22px;
  color: black;
  background-color: rgba(209, 209, 209, 0.322);
}
button:hover {
  color: rgb(255, 255, 255);
  background-color: rgba(0, 0, 0, 0.459);
}
.container {
  width: 80%;
  height: calc(100vh - 94px);
  margin: 0 auto;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  gap: 26px;
}
.imgContainer {
  width: 356px;
  height: 256px;
  border-radius: 20px;
  overflow: hidden;
}
.imgContainer > img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: all 0.3s ease-in-out;
}
.imgContainer:hover > img {
  transform: scale(1.2);
}
.slideContainer {
  width: 812px;
  height: 512px;
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  overflow: hidden;
  z-index: 2;
}
.slider {
  width: 812px;
  display: flex;
}
.item {
  width: 812px;
  height: 512px;
}
.item > img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  overflow: hidden;
  border-radius: 20px;
}
</style>
