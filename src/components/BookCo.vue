<template>
  <div class="books">
    <div class="container">
      <div
        v-for="(book, index) in books"
        :key="index"
        class="book"
        :class="{ pending: book.status == 1 }"
      >
        <div class="img">
          <img :src="require(`@/assets/books/${book.img}`)" alt="" />
        </div>
        <h4>
          {{ book.name }}
        </h4>
      </div>
    </div>
  </div>
</template>

<script setup>
import { inject } from "vue";
const data = inject("data");
let books = data.value.books;
</script>

<style scoped>
.books {
  background: #220c59;
}
.books .container {
  width: 80%;
  margin: 50px auto;
  color: white;
  display: flex;
  flex-wrap: wrap;
  align-items: flex-start;
  justify-content: center;
}
.book {
  width: 180px;
  padding: 10px;
  background: #0f0939;
  border-radius: 5px;
  position: relative;
  margin: 5px 15px;
  /* transition: all 0.5s linear; */
}
/* .book:hover {
    transform: scale(1.1);
} */
.book .img {
  width: 100%;
}
.book h4 {
  width: 100%;
}
.book .img img {
  width: 100%;
}

.book.pending::before {
  content: "Bending";
  position: absolute;
  top: -20px;
  background: #7e0c61;
  left: 10px;
  border-top-left-radius: 10px;
  border-top-right-radius: 10px;
  width: calc(100% - 20px);
}
</style>
