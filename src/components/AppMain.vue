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
  <main class="container">
    <AppCard v-for="movie in store.movies" :content="movie"/>
    <AppCard v-for="serie in store.tvSeries" :content="serie"/>
  </main>
</template>

<style lang="scss" scoped>

.container {

  margin: 0 auto;

  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
}
</style>