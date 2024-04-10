<template>
  <div class="articles">
    <div class="container">
      <div class="articles-container">
        <div class="article" v-for="article in articles" :key="article.id">
          <a :href="article.link" target="_blank">
            <div class="img">
              <img v-if="article.link.includes('hashnode')"
              src="@/assets/link/hashnode.png" alt="" />
              <img v-if="article.link.includes('medium')"
              src="@/assets/link/medium.png" alt="" />
            </div>
            <h3>{{ article.title }}</h3></a
          >
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { inject } from "vue";
const data = inject("data");
let articles = data.value.articles;
</script>

<style scoped>
.articles {
  background: #220c59;
}
.articles .container {
  width: 60%;
  margin: 20px auto;
  color: white;
}
.article {
  margin: 10px;
  width: fit-content;
}
.article a {
  color: white;
  display: flex;
  align-items: center;
}
.article h3 {
  margin-left: 20px;
}
.article .img {
  width: 40px;
}
.article .img img {
  width: 100%;
}
</style>
