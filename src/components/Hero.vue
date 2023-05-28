<script setup>
import { defineProps, defineEmits } from "vue";

const { isRickAndMorty } = defineProps(["isRickAndMorty"]);

const emit = defineEmits(["changeMovie"]);

const emitChangeMovie = () => {
  emit("changeMovie");
};
</script>

<template>
  <div class="hero">
    <h1>{{ isRickAndMorty ? "Rick and Morty" : "Game of Thrones " }}</h1>
    <p @click="emitChangeMovie">
      {{ isRickAndMorty ? "Game of Thrones" : "Rick and Morty " }}
    </p>
  </div>
</template>

<style scoped>
.hero {
  height: 40vh;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  flex-direction: column;
}

.hero img {
  position: absolute;
  height: 700px;
  opacity: 0.1;
}

.hero h1 {
  font-size: 80px;
  font-weight: bold;
}

.hero p {
  cursor: pointer;
}
</style>
