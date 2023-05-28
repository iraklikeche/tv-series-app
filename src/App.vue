<script setup>
import RickAndMortyCard from "./components/RickAndMortyCard.vue";
import GOTCard from "./components/GOTCard.vue";
</script>

<template>
  <main>
    <h1>HERO</h1>
    <Suspense>
      <template #default>
        <RickAndMortyCard />
      </template>
      <template #fallback>
        <div>
          <p>Loading...</p>
        </div>
      </template>
    </Suspense>
    <GOTCard />
  </main>
</template>

<style scoped></style>
