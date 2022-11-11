<template>
  <div>
    <div class="col">
      <div class="card h-100">
        <img :src="poster_path" class="card-img-top">
        <div class="card-body">
          <h5 class="card-title fw-bold">{{ movie.title }}</h5>
          <p class="card-text">{{ overview }}</p>
        </div>
      </div>
    </div>
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