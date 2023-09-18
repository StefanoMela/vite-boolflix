<script>
import { store } from "../data/store";

import AppCard from './AppCard.vue'

export default {

  data() {
    return {
      store,
    }
  },

components: { AppCard }
};
</script>

<template>
  <main class="container-fluid">
    <h3 class="text-center">Movies</h3>
    <section class="movie container">
      <AppCard v-for="movie in store.movies" :content="movie"/>
    </section>
    <h3 class="text-center my-3">Tv Series</h3>
    <section class="tv-series container">
      <AppCard v-for="serie in store.tvSeries" :content="serie"/>
    </section>
  </main>
</template>

<style lang="scss" scoped>

  .container{
    display: flex;
    flex-wrap: wrap;
    gap: 1rem;
  }
</style>