<script>
import { store } from "../data/store";

export default {
  data() {
    return {
      store,
    };
  },
};
</script>

<template>
  <div v-for="movie in store.movies" class="card">
    <img class="card-img-top" />
    <div class="card-body">
      <h5 class="card-title">Titolo: {{movie.title}}</h5>
      <h5 class="card-title">Titolo Orginale: {{movie.original_title}}</h5>
      <span><strong>Lingua: </strong> {{ movie.original_language }}</span><br>
      <span><strong>Voto: </strong> {{ movie.vote_average }}</span>
      <p class="card-text"><strong>Descrizione:</strong> {{ movie.overview }}</p>
    </div>
  </div>
  <div v-for="serie in store.tvSeries" class="card">
    <img class="card-img-top" />
    <div class="card-body">
      <h5 class="card-title">Titolo: {{serie.name}}</h5>
      <h5 class="card-title">Titolo Originale: {{serie.original_name}}</h5>
      <span><strong>Lingua: </strong> {{ serie.original_language }}</span><br>
      <span><strong>Voto: </strong> {{ serie.vote_average }}</span>
      <p class="card-text"><strong>Descrizione: </strong>{{ serie.overview }}</p>
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
