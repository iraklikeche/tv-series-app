<script setup>
import RickAndMortyCard from "./components/RickAndMortySuspense.vue";
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

    <KeepAlive>
      <Component :is="isRickAndMorty ? RickAndMortyCard : GOTCard" />
    </KeepAlive>
  </main>
</template>
