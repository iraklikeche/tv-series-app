<script setup>
import { ref, watch } from "vue";
import axios from "axios";
import Card from "./Card.vue";

const characters = ref(null);
const page = ref(1);

const response = await axios.get("https://rickandmortyapi.com/api/character");
characters.value = response.data.results;

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
        :species="character.species"
      />
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
</style>
