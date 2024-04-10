<template>
  <div>
    <MainCo v-if="datafetched" />
    <div class="component">
      <div class="titles">
        <p
          @click="selected = 'Experience'"
          :class="{ selected: selected == 'Experience' }"
        >
          Experience
        </p>
        <p
          @click="selected = 'SkillsCo'"
          :class="{ selected: selected == 'SkillsCo' }"
        >
          Skills
        </p>
        <p
          @click="selected = 'Projects'"
          :class="{ selected: selected == 'Projects' }"
        >
          Projects
        </p>
        <p
          @click="selected = 'Articles'"
          :class="{ selected: selected == 'Articles' }"
        >
          Articles
        </p>
        <p
          @click="selected = 'Books'"
          :class="{ selected: selected == 'Books' }"
        >
          Books
        </p>
        <p
          @click="selected = 'ContributS'"
          :class="{ selected: selected == 'ContributS' }"
        >
          Contributions
        </p>
      </div>
    </div>
    <SkillsCo v-if="datafetched"
      class="notselectedcomponent"
      :class="{ selectedcomponent: selected == 'SkillsCo' }"
    />
    <Projects v-if="datafetched"
      class="notselectedcomponent"
      :class="{ selectedcomponent: selected == 'Projects' }"
    />
    <Articles v-if="datafetched"
      class="notselectedcomponent"
      :class="{ selectedcomponent: selected == 'Articles' }"
    />
    <Books v-if="datafetched"
      class="notselectedcomponent"
      :class="{ selectedcomponent: selected == 'Books' }"
    />
    <Contributions v-if="datafetched"
      class="notselectedcomponent"
      :class="{ selectedcomponent: selected == 'ContributS' }"
    />
    <Experience v-if="datafetched"
      class="notselectedcomponent"
      :class="{ selectedcomponent: selected == 'Experience' }"
    />
  </div>
</template>

<script setup>

import { ref, provide } from "vue";
const data = ref({});
provide("data", data);
const datafetched = ref(false);
const FetchData = async () => {
  const response = await fetch("/data.json");
  const jsonData = await response.json();
  data.value = jsonData;
  datafetched.value = true;

};
FetchData();
// eslint-disable-next-line no-unused-vars
import MainCo from "@/components/MainCo.vue";
// eslint-disable-next-line no-unused-vars
import SkillsCo from "@/components/SkillsCo.vue";
// eslint-disable-next-line no-unused-vars
import Projects from "@/components/ProjectsCo.vue";
// eslint-disable-next-line no-unused-vars
import Articles from "@/components/ArticlesCo.vue";
// eslint-disable-next-line no-unused-vars
import Books from "@/components/BookCo.vue";
// eslint-disable-next-line no-unused-vars
import Contributions from "@/components/ContributionsCo.vue";
// eslint-disable-next-line no-unused-vars
import Experience from "@/components/ExperienceCo.vue";
let selected = ref("Experience");
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Edu NSW ACT Foundation", cursive;
}

body {
  overflow-x: hidden;
  scrollbar-width: thin;
  scrollbar-color: #888 #f1f1f1;
}
/* This will affect the scrollbar globally */
body::-webkit-scrollbar {
  width: 10px; /* width of the entire scrollbar */
}

body::-webkit-scrollbar-track {
  background: #f1f1f1; /* color of the tracking area */
}

body::-webkit-scrollbar-thumb {
  background: #888; /* color of the scroll thumb */
}

body::-webkit-scrollbar-thumb:hover {
  background: #555; /* color of the scroll thumb on hover */
}

.component {
  background: #220c59;
  width: 100vw;
}

.component .titles {
  display: flex;
  justify-content: space-around;
  align-items: center;
  color: white;
  font-size: 25px;
  padding: 10px 0px;
}
@media (max-width: 768px) {
  .component .titles {
    font-size: 20px;
    flex-direction: column;
  }
  .titles p {
    width: 100%;
  }
}
.titles p {
  flex-grow: 1;
  padding: 10px 0px;
  cursor: pointer;
}
.titles p.selected {
  background: linear-gradient(
    92.88deg,
    #455eb5 9.16%,
    #5643cc 43.89%,
    #673fd7 64.72%
  );
  border-bottom-left-radius: 15px 255px;
  border-bottom-right-radius: 225px 15px;
  border-top-left-radius: 255px 15px;
  border-top-right-radius: 15px 225px;
}
.notselectedcomponent {
  max-height: 0;
  transition: max-height 0.5s ease-out;
  overflow: hidden;
  width: 100vw;
}
.selectedcomponent {
  max-height: 2300px;
}
</style>
