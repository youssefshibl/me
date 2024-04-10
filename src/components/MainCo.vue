<template>
  <div class="outercontainer" @mousemove="moveObjects">
    <div class="layer"></div>
    <div class="layer"></div>
    <div class="layer"></div>
    <div class="layer"></div>
    <div class="layer"></div>
    <div class="layer"></div>
    <div class="layer"></div>

    <div class="head">
      <div class="left">
        <div class="imgbox">
          <img class="avatar" src="../assets/pernsonal/me.jpg" alt="" />
        </div>
        <div class="name">
          <h1>{{ data.personal.name }}</h1>
          <h3>{{ data.personal.title }}</h3>
          <div class="links">
            <a :href="links.github" target="_blank">
              <img src="@/assets/pernsonal/icons8-github-48.png" alt="" />
            </a>
            <a :href="links.linkedin" target="_blank">
              <img
                src="@/assets/pernsonal/icons8-linkedin-48.png"
                alt="LinkedIn"
              />
            </a>
            <a :href="links.gmail" target="_blank">
              <img src="@/assets/pernsonal/gmail.png" alt="Gmail" />
            </a>
            <a :href="links.leetcode" target="_blank">
              <img src="@/assets/pernsonal/leetcode.png" alt="LeetCode" />
            </a>
            <a :href="links.hashnode" target="_blank">
              <img src="@/assets/pernsonal/hashnode.png" alt="Hashnode" />
            </a>
            <a :href="links.twitter" target="_blank">
              <img src="@/assets/pernsonal/twitter.png" alt="Twitter" />
            </a>
            <a :href="links.facebook" target="_blank">
              <img src="@/assets/pernsonal/facebook.png" alt="Facebook" />
            </a>
          </div>
          <h4>
            ``You don't have to be great to start, but you have to start to be
            great.``
          </h4>
        </div>
      </div>
      <div class="right"></div>
    </div>
    <div class="skils">
      <div class="left-side"></div>
      <div class="right-side"></div>
      <div class="item-box-one">
        <div
          v-for="(skill, image, index) in skills"
          class="img-box"
          :key="index"
        >
          <img :src="require(`@/assets/skills/${skill}`)" alt="" />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { inject } from "vue";
const data = inject("data");
const links = data.value.personal.links;
const skills = data.value.skills;
// move objects with curser function
function moveObjects(e) {
  const { clientX, clientY } = e;
  const halfHeight = window.innerHeight / 2;
  const halfWidth = window.innerWidth / 2;
  const halfX = clientX - halfWidth;
  const halfY = clientY - halfHeight;
  // all .layer expect the first one
  const layers = document.querySelectorAll(".layer");
  layers.forEach((layer, index) => {
    if (index === 0) return;
    const divider = index / 100;
    const offsetX = halfX * divider;
    const offsetY = halfY * divider;
    const transform = `translate(${offsetX}px, ${offsetY}px)`;
    layer.style.transform = transform;
  });
}
</script>

<style scoped>
.outercontainer {
  width: 100vw;
  height: 100vh;
  background: linear-gradient(195deg, #110e50 40%, #220c59 75%);
  overflow: hidden;
}
.head {
  display: flex;
  justify-content: space-around;
  padding-top: 100px;
  position: relative;
  flex-wrap: wrap;
}
.head .left {
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  justify-content: center;
}
.left .imgbox {
  width: 150px;
  height: 150px;
  border-radius: 50%;
  border: 6px solid #e30f8329;
  overflow: hidden;
  border-style: outset;
}
.left .avatar {
  width: 150px;
}
.left .name {
  margin-left: 40px;
  color: white;
  font-weight: bold;
  text-align: start;
}

.name h1 {
  font-size: 2rem;
  text-shadow: -1px -1px 3px #ffffff3b, 2px 2px 4px #ffffff54;
}

.name h3 {
  font-weight: 100;
}
.links {
  margin-top: 20px;
}
.name h4 {
  margin-top: 20px;
}

.outercontainer .layer {
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  z-index: 0;
  margin: 0px;
  padding: 0px;
  height: 100%;
  background-size: cover;
}

.outercontainer .layer:nth-child(1) {
  background: url("../assets//pernsonal/1.png");
  animation: animate 100s ease-in-out infinite;
  background-size: contain;
  background-repeat: no-repeat;
}
@keyframes animate {
  0% {
    background-position: 0px 0px;
  }
  25% {
    background-position: 250px 200px;
  }
  50% {
    background-position: 500px -200px;
  }
  75% {
    background-position: 750px 100px;
  }
  100% {
    background-position: 1000px 0px;
  }
}
.outercontainer .layer:nth-child(2) {
  background: url("../assets//pernsonal/2.png");
  background-position: 0px -100px;
}
.outercontainer .layer:nth-child(3) {
  background: url("../assets//pernsonal/3.png");
  background-position: 0px -100px;
}
.outercontainer .layer:nth-child(4) {
  background: url("../assets//pernsonal/4.png");
  background-position: 0px -100px;
}
.outercontainer .layer:nth-child(5) {
  background: url("../assets//pernsonal/5.png");
  background-position: 0px -100px;
}
.outercontainer .layer:nth-child(6) {
  background: url("../assets//pernsonal/6.png");
  background-position: 0px -100px;
}
.outercontainer .layer:nth-child(7) {
  background: url("../assets//pernsonal/7.png");
  background-position: 0px -100px;
}
.skils {
  height: 80px;
  background: linear-gradient(0deg, #00000078, #0000009c, #00000078);
  margin-top: 100px;
  position: relative;
  width: 100vw;
  margin-left: auto;
  margin-right: auto;
  overflow: hidden;
}

.img-box {
  width: 50px;
  display: inline-block;
  margin: 0px 25px;
}

.img-box img {
  width: 100%;
  height: 100%;
}

.item-box-one {
  white-space: nowrap;
  width: fit-content;
  animation: 30s linear 0s infinite normal none running marqueeAnimation-6668070;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
}
.item-box-one:hover {
  animation-play-state: paused;
}

@keyframes marqueeAnimation-6668070 {
  0% {
    transform: translateX(100vw);
  }
  100% {
    transform: translateX(calc(-100%));
  }
}

.left-side {
  pointer-events: none;
  width: 20%;
  height: 100%;
  position: absolute;
  z-index: 999;
  left: 0;
  background: linear-gradient(90deg, #220c59, #110e5000);
}
.right-side {
  pointer-events: none;
  width: 20%;
  height: 100%;
  position: absolute;
  z-index: 999;
  right: 0;
  background: linear-gradient(90deg, #110e5000, #150e52);
}
</style>
