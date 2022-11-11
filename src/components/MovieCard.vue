<template>
  <div>
    <img :src="poster_path" alt="영화 포스터">
    <h3>{{ movie.title }}</h3>
    <p>{{ overview }}</p>
  </div>
</template>

<script>
export default {
  name: 'MovieCard',
  data(){
    return{
      poster_path: `https://www.themoviedb.org/t/p/w300_and_h450_bestv2/${this.movie.poster_path}`,
      overview: this.movie.overview.slice(0, 100) + '...',
    }
  },
  props: {
    movie: Object,
  }
}
</script>

<style>

</style>