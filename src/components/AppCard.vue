<script>
export default {
  props: {
    content: Object
  },
};
</script>

<template>
  <div class="card">
    <img class="card-img-top"
    />
    <div class="card-body">
      <h5 class="card-title">Titolo: {{ content.title }}</h5>
      <h5 class="card-title">Titolo Orginale: {{ content.original_title }}</h5>
      <span><strong>Lingua: </strong> {{ content.original_language }}</span
      ><br />
      <span><strong>Voto: </strong> {{ content.vote_average }}</span>
      <p class="card-text">
        <strong>Descrizione:</strong> {{ content.overview }}
      </p>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.card {
  width: calc((100% / 4) - 1rem);
  aspect-ratio: 1;
  overflow: auto;
  cursor: pointer;
}
</style>
