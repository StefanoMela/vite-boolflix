<script>
export default {

  data() {
    return {
      queryString: '',
    }
  },

  emits: ["form-submit"]

};
</script>

<template>
<nav class="navbar bg-body-tertiary mb-5">
  <div class="container">
    <a class="navbar-brand">Boolflix</a>
    <form 
    @submit.prevent="$emit('form-submit',queryString)"
    class="d-flex" role="search">
      <input 
      v-model="queryString"
      class="form-control me-2" type="search" placeholder="Search" aria-label="Search">
      <button class="btn btn-outline-success" type="submit">Search</button>
    </form>
  </div>
</nav>
</template>

<style lang="scss" scoped>
</style>