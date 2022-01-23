<template>
  <div class="home">
    <div class="fname">
      <span class="contain" v-for="item in fname.split('')" :key="item"
        ><p class="text">{{ item }}</p></span
      >
    </div>
    <div class="lname">
      <span v-for="item in lname.split('')" :key="item"
        ><p class="text">{{ item }}</p></span
      >
    </div>
    <div class="position">
      <span v-for="item in position.split('')" :key="item"
        ><p class="text">{{ item }}</p></span
      >
    </div>
    <div class="about">
      <p>
        I'm a front-end web developer. I am passionate about developing web
        front end with javascript and css and I am also interested in back end
        developer, and devops. I want to develop myself to the highest I can
        reach before I retire.
      </p>
    </div>
    <div class="getin">
      <div class="marquee">
        <p>GET IN TOUCH WITH ME</p>
        <div class="marquee__inner" aria-hidden="true">
          <span>taechasit.bjr@gmail.com</span>
          <span>taechasit.bjr@gmail.com</span>
          <span>taechasit.bjr@gmail.com</span>
          <span>taechasit.bjr@gmail.com</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Home",
  data() {
    return {
      fname: "TAECHASIT",
      lname: "BOONJAROEN",
      position: "FRONT - END DEVELOPER",
    };
  },
};
</script>
<style scoped>
.home {
  height: calc(100vh - 94px);
}
span:not(.text) {
  font-size: 6vw;
  margin: 0 8px;
  overflow: hidden;
}
.contain {
  position: relative;
}
.fname,
.lname,
.position {
  display: flex;
  border-bottom: 1px solid rgb(56, 56, 56);
}
.fname .text,
.position .text {
  transform: translateX(-102px);
  animation: toright 1s ease-in-out forwards;
}
.lname {
  justify-content: flex-end;
}
.lname .text {
  transform: translateX(102px);
  animation: toleft 1s ease-in-out 0.2s forwards;
}
.about {
  font-size: 32px;
  width: 50%;
  margin: 56px;
  overflow: hidden;
}
.about p {
  animation: toup 1s ease-in-out 1s forwards;
  transform: translateY(150px);
}
.getin {
  margin: 26px;
  height: 204px;
  display: flex;
  justify-content: flex-end;
  align-items: center;
}

@keyframes toright {
  from {
    transform: translateX(-102px);
  }
  to {
    transform: translateX(0);
  }
}
@keyframes toleft {
  from {
    transform: translateX(102px);
  }
  to {
    transform: translateX(0);
  }
}
@keyframes toup {
  from {
    transform: translateY(150px);
  }
  to {
    transform: translateX(0);
  }
}

.marquee {
  position: relative;
  max-width: 100vw;
  overflow: hidden;
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
  animation: marquee 5s linear infinite;
  animation-play-state: paused;
}

.marquee span:not(.dot) {
  font-size: 9vw;
  padding: 0 1vw;
  font-family: "Anton", sans-serif;
}
.marquee:hover > p {
  display: none;
}
</style>
