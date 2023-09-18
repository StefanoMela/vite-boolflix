<script>
export default {


  data() {
    return {
      imgUrl: 'https://image.tmdb.org/t/p/w342',
      noPosterPath: '/no-poster.jpg'
    }
  },

  props: {
    content: Object,
  },

  computed: {
    hasFlag() {
      const allowedflags = ["en", "it"];
      return allowedflags.includes(this.content.original_language);
    },

    flagSrc() {
      const flagUrl = new URL(
        `../assets/img/${this.content.original_language}.png`,
        import.meta.url
      );

      return flagUrl.href;
    },

    posterSrc () {
      if(!this.content.poster_path) return `${this.noPosterPath}`
      return `${this.imgUrl}${this.content.poster_path}`
    },    
      averageStars () {
        return Math.ceil(this.content.vote_average / 2);
      },
  },

  methods: {

    starClass (n) {
      return n <= this.averageStars ? 'fa-solid fa-star' : 'fa-regular fa-star';
    },

  },

};
</script>

<template>
  <div class="card">
    <img class="card-img-top"
    :src="posterSrc" :alt="content.overview"/>
    <div class="card-body">
      <h5 class="card-title">Titolo: {{ content.title }}</h5>
      <h6 class="card-subtitle my-1">
        Titolo Orginale: {{ content.original_title }}
      </h6>
      <div v-if="hasFlag">
        <h6>Lingua:</h6>
        <img :src="flagSrc" :alt="content.original_language" />
      </div>
      <span>
        <strong>Voto:</strong>
        <font-awesome-icon :icon="starClass(n)" v-for="n in 5" />
        {{ content.vote_average }}
      </span>
      <p class="card-text">
        <strong>Descrizione:</strong> {{ content.overview }}
      </p>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.card {
  width: calc((100% / 4) - 1rem);
  overflow: auto;
  cursor: pointer;

}
</style>
