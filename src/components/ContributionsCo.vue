<template>
  <div class="contributions">
    <div class="container">
      <div
        class="contribution"
        v-for="(contribution, index) in contributions"
        :key="index"
      >
        <a target="_blank" :href="contribution.url"
          ><h3>{{ contribution.name }}</h3></a
        >
        <div class="prs">
          <a
            target="_blank"
            v-for="(rp, index) in contribution.PR"
            :key="index"
            :href="rp"
            >PR{{ index + 1 }}</a
          >
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { inject } from "vue";
const data = inject("data");
let contributions = data.value.contributions;
</script>

<style scoped>
.contributions {
  background: #220c59;
}
.contributions .container {
  width: 80%;
  margin: 50px auto;
  color: white;
  display: flex;
  flex-wrap: wrap;
}

.contribution {
  background: #0f0939;
  padding: 10px 10px;
  width: 100%;
  text-align: start;
  border-radius: 5px;
  color: white;
}

.contribution a {
  text-decoration: none;
  color: white;
}
.prs {
  margin: 20px 10px 5px 10px;
}

.prs a {
  padding: 1px 16px;
  margin: 5px 20px;
  background: #3178c6;
  border-radius: 11px;
}

.prs a:hover {
  background: #1d4a7a;
}
</style>
