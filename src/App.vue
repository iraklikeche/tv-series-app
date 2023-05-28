<script setup>
import RickAndMortyCard from "./components/RickAndMortyCard.vue";
import GOTCard from "./components/GOTCard.vue";
import Hero from "./components/Hero.vue";
import { ref } from "vue";

const isRickAndMorty = ref(true);
</script>

<template>
  <main>
    <Hero
      :isRickAndMorty="isRickAndMorty"
      @changeMovie="isRickAndMorty = !isRickAndMorty"
    />
    <Suspense v-if="isRickAndMorty">
      <template #default>
        <RickAndMortyCard />
      </template>
      <template #fallback>
        <div class="cards spinner">
          <NSpin size="large" />
        </div>
      </template>
    </Suspense>
    <GOTCard v-else />
  </main>
</template>

<style scoped>
.cards {
  height: 700px;
  background-color: rgb(27, 26, 26);
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
