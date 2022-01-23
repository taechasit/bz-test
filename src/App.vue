<template>
  <div id="app">
    <div id="nav">
      <div class="navContainer">
        <div class="name">TAECHASIT</div>
        <div class="inner">
          <div class="marquee" @click="goto('/')">
            <router-link to="/">PROFILE</router-link>
            <div class="marquee__inner" aria-hidden="true">
              <span>PROFILE</span>
              <span class="dot"></span>
              <span>PROFILE</span>
              <span class="dot"></span>
              <span>PROFILE</span>
              <span class="dot"></span>
              <span>PROFILE</span>
              <span class="dot"></span>
            </div>
          </div>
          <div class="marquee" @click="goto('/imgs')">
            <router-link to="/imgs">GALLERY</router-link>
            <div class="marquee__inner" aria-hidden="true">
              <span>GALLERY</span>
              <span class="dot"></span>
              <span>GALLERY</span>
              <span class="dot"></span>
              <span>GALLERY</span>
              <span class="dot"></span>
              <span>GALLERY</span>
              <span class="dot"></span>
            </div>
          </div>
        </div>
      </div>
    </div>

    <router-view />
  </div>
</template>
<script>
export default {
  name: "App",
  methods: {
    goto(path) {
      this.$router.push({ path: path });
    },
  },
};
</script>
<style>
@import url("https://fonts.googleapis.com/css2?family=Luxurious+Roman&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Anton&family=Luxurious+Roman&display=swap");
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  background-color: black;
  color: white;
  font-family: "Luxurious Roman", cursive;
}
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
#nav {
  height: 94px;
  border-bottom: 1px solid white;
}
.inner {
  height: 100%;
  display: flex;
  justify-content: end;
  align-items: center;
}
.navContainer {
  height: 100%;
  width: 80%;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.navContainer .marquee {
  text-decoration: none;
  margin: 0 18px;
  border: 1px solid white;
  padding: 12px;
  border-radius: 20px;
}
a {
  text-decoration: none;
}

.marquee {
  position: relative;
  overflow: hidden;
  max-width: 126px;
  --offset: 3.6vw;
  --move-initial: calc(-25% + var(--offset));
  --move-final: calc(-50% + var(--offset));
}

.marquee__inner {
  width: fit-content;
  transition: all 5s ease-in-out;
  display: none;
  position: relative;
  transform: translate3d(var(--move-initial), 0, 0);
  animation: marquee 2s linear infinite;
  animation-play-state: paused;
}

.marquee span:not(.dot) {
  font-size: 13px;
  padding: 0 1vw;
  font-family: "Anton", sans-serif;
}

.marquee:hover .marquee__inner {
  animation-play-state: running;
  display: flex;
}
.marquee:hover > a {
  display: none;
}
.name {
  font-size: 28px;
}
.dot {
  height: 10px;
  width: 10px;
  margin-top: 4px;
  background-color: rgb(255, 255, 255);
  border-radius: 50%;
  display: inline-block;
}
@keyframes marquee {
  0% {
    transform: translate3d(var(--move-initial), 0, 0);
  }

  100% {
    transform: translate3d(var(--move-final), 0, 0);
  }
}
</style>
