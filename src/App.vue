<script>
import axios from 'axios';
import { store } from "./data/store.js";


import AppMain from './components/AppMain.vue'
import AppHeader from './components/AppHeader.vue'

export default {
  data() {
    return {
      store,

      apiKey: 'a08a8688fcc51d832aa56ad09708bd23',
      moviesEndpoint: 'https://api.themoviedb.org/3/search/movie',
      tvSeriesEndpoint: 'https://api.themoviedb.org/3/search/tv',
    }
  },

  components: { AppMain, AppHeader },

  methods: {

    fetchMovies(moviesEndpoint) {
      axios.get(moviesEndpoint).then((response) => {
        store.movies = response.data.results.map((movie)=> {

          const { id, original_language, original_title, overview, poster_path, title, vote_average } = movie;
          return { id, original_language, original_title, overview, poster_path, title, vote_average };
        });
      }
    )},
    fetchTvSeries(tvSeriesEndpoint) {
      axios.get(tvSeriesEndpoint).then((response) => {
        store.tvSeries = response.data.results.map((tvSerie)=> {

          const { id, original_language, original_name, overview, poster_path, name, vote_average } = tvSerie;
          return { id, original_language, original_name, overview, poster_path, name, vote_average };
        });
      }
    )},
  },

  handleSearch(queryString) {
      // il parametro può anche cambiare nome rispetto al nome del componente
      const moviesSearchEndpoint = `${this.moviesEndpoint}${this.apiKey}${queryString}`;
      this.fetchMovies(moviesSearchEndpoint);
    },

  created() {
    this.fetchMovies(this.moviesEndpoint)
    this.fetchTvSeries(this.tvSeriesEndpoint)
  }
};
</script>

<template>
  <AppHeader 
  @form-submit="handleSearch"/>
  <AppMain />
</template>

<style lang="scss" scoped></style>
