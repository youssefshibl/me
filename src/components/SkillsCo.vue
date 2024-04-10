<template>
  <div class="skills">
    <div class="container">
      <div
        v-for="(image, skill, index) in skills"
        class="img-box tag"
        :key="index"
      >
        {{ skill }}
      </div>
    </div>
  </div>
</template>

<script setup>
import { inject } from "vue";
const data = inject("data");
let skills = data.value.skills;
</script>

<style scoped>
.skills {
  background: #220c59;
}
.skills .container {
  width: 80%;
  margin: 20px auto;
}
.tag {
  position: relative;
  display: inline-block;
  border-radius: 6px;
  clip-path: polygon(20px 0px, 100% 0px, 100% 100%, 0% 100%, 0% 20px);
  background: #140735;
  padding: 5px 30px;
  margin: 10px 8px;
  font-weight: 600;
  font-size: 18px;
  color: #220c59;
  transition: clip-path 500ms;
  color: white;
}

.tag:after {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 20px;
  height: 20px;
  background: #5aaa46;
  box-shadow: 2px 2px 2px rgba(0, 0, 0, 0.1);
  border-radius: 0 0 6px 0;
  transition: transform 500ms;
}

.tag:hover {
  clip-path: polygon(0px 0px, 100% 0px, 100% 100%, 0% 100%, 0% 0px);
}

.tag:hover:after {
  transform: translate(-100%, -100%);
}
</style>


