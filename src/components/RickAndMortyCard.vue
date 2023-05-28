<script setup>
import { ref, watch } from "vue";
import axios from "axios";
import Card from "./Card.vue";

const characters = ref(null);
const page = ref(1);
const pages = ref(null);

const response = await axios.get("https://rickandmortyapi.com/api/character");
characters.value = response.data.results;
pages.value = response.data.info.pages;

console.log(pages.value);

watch(page, async () => {
  const res = await axios.get(
    `https://rickandmortyapi.com/api/character/?page=${page.value}`
  );
  characters.value = res.data.results;
});

console.log(response);

const nextPage = () => {
  page.value += 1;
  console.log(page.value);
};
const previousPage = () => {
  page.value -= 1;
  console.log(page.value);
};
</script>

<template>
  <div class="container">
    <div class="cards">
      <Card
        v-for="character in characters"
        :key="character.id"
        :image="character.image"
        :name="character.name"
      >
        <p>{{ character.location.name }}</p>
      </Card>
    </div>
    <div class="button-container">
      <button @click="previousPage" :disabled="page === 1">&lt;</button>
      <button @click="nextPage" :disabled="page === pages">></button>
    </div>
  </div>
</template>

<style scoped>
.container {
  background-color: rgb(27, 26, 26);
  padding: 30px;
}

.cards {
  max-width: 1000px;
  margin: 0 auto;
  display: flex;
  flex-wrap: wrap;
}

.button-container {
  display: flex;
  justify-content: center;
  padding-top: 30px;
}

.button-container button {
  border: none;
  width: 50px;
  height: 50px;
  border-radius: 100%;
  margin: 0 5px;
  cursor: pointer;
}
</style>
