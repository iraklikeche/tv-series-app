<script setup>
import { ref, watch, onMounted } from "vue";
import axios from "axios";
import Card from "./Card.vue";

const characters = ref(null);

onMounted(async () => {
  const response = await axios.get("https://thronesapi.com/api/v2/Characters");
  console.log(response);
  characters.value = response.data;
});

// watch(page, async () => {
//   const res = await axios.get(
//     `https://rickandmortyapi.com/api/character/?page=${page.value}`
//   );
//   characters.value = res.data.results;
// });

// const nextPage = () => {
//   page.value += 1;
//   console.log(page.value);
// };
// const previousPage = () => {
//   page.value -= 1;
//   console.log(page.value);
// };
</script>

<template>
  <div class="container">
    <div class="cards">
      <Card
        v-for="character in characters"
        :key="character.id"
        :image="character.imageUrl"
        :name="character.fullName"
      >
        <p>{{ character.title }}</p>
      </Card>
    </div>
    <div class="button-container"></div>
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
