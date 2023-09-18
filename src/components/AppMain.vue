<script>
import AppCard from './AppCard.vue'

export default {
components: { AppCard }
};
</script>

<template>
  <main class="container">
    <AppCard />
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