<template>
  <div class="projects">
    <div class="container">
      <div class="project" v-for="(project, index) in projects" :key="index">
        <div class="content">
          <div class="title">
            <h3>{{ project.name }}</h3>
            <div class="icons">
              <a
                v-for="(value, key, index) in project.links"
                :key="index"
                :href="value"
                target="_blank"
              >
                <img :src="require(`@/assets/link/${key}.png`)" alt="" />
              </a>
            </div>
          </div>
          <p>{{ project.description }}</p>
          <div class="stacks">
            <span v-for="(stack, index) in project.stacks" :key="index">
              {{ stack }}
            </span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { inject } from "vue";
const data = inject("data");
let projects = data.value.projects;
</script>

<style>
.projects {
  background: #220c59;
}
.projects .container {
  width: 60%;
  margin: 20px auto;
  color: white;
}
.container .project {
  margin: 10px 0px;
}
.container .content {
  text-align: start;
  padding: 15px;
  background: #140735;
  border-radius: 5px;
}

.content p {
  margin-top: 10px;
}
.stacks {
  margin-top: 20px;
  margin-bottom: 5px;
  text-align: end;
  display: flex;
  flex-wrap: wrap;
}
.stacks span {
  padding: 1px 10px;
  background: linear-gradient(
    92.88deg,
    #455eb5 9.16%,
    #5643cc 43.89%,
    #673fd7 64.72%
  );
  border-radius: 2px;
  margin: 5px 10px;
}
.title {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.title .icons a {
  width: 25px;
  display: inline-block;
  margin: 0px 10px;
}
.title .icons a img {
  width: 100%;
}
</style>
