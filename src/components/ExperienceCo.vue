<template>
  <div class="articles">
    <div class="container">
      <div class="experiencecontainer">
        <div class="experience" v-for="(exp, index) in experience" :key="index">
          <div class="title">{{ exp.title }} @ {{ exp.company }}</div>
          <div class="metadata">
            <div class="date">{{ exp.from }} - {{ exp.to }}</div>
            <div class="location">
              {{ exp.location }}
            </div>
            <div class="type">
              {{ exp.type }}
            </div>
          </div>
          <div class="description">
            {{ exp.description }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { inject } from "vue";
const data = inject("data");
let experience = data.value.experience;
</script>

<style scoped>
.articles {
  background: #220c59;
}
.articles .container {
  width: 60%;
  margin: 40px auto;
  color: white;
}
.experience {
  text-align: start;
  padding: 20px 10px 20px 60px;
  background: #140735;
  border-radius: 5px;
  position: relative;
  margin: 20px 0px;
}
.experience::before {
  content: "";
  position: absolute;
  width: 20px;
  height: 20px;
  background: white;
  border-radius: 50%;
  left: 20px;
  top: 50%;
  transform: translateY(-50%);
}
.experience::after {
  content: "";
  position: absolute;
  width: 2px;
  height: 112%;
  background: white;
  left: 30px;
  bottom: 0;
}
.experience .title {
  font-size: 22px;
}
.metadata {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.metadata div {
  margin: 10px 0px 10px 20px;
  color: #ffffff9c;
}
</style>
