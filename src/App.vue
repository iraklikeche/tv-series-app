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
        <div class="cards spinner">
          <NSpin size="large" />
        </div>
      </template>
    </Suspense>
    <GOTCard />
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
