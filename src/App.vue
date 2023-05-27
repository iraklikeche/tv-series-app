<script setup>
import TvSeriesCard from "./components/TvSeriesCard.vue";
</script>

<template>
  <main>
    <h1>HERO</h1>
    <Suspense>
      <template #default>
        <TvSeriesCard />
      </template>
      <template #fallback>
        <div>
          <p>Loading...</p>
        </div>
      </template>
    </Suspense>
  </main>
</template>

<style scoped></style>
