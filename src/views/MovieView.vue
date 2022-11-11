<template>
  <div class="movie">
    <h1>뀰movie</h1>
    <MovieCard/>
  </div>
</template>

<script>
import MovieCard from '@/components/MovieCard'

export default {
  name: 'MovieView',
  components: {
    MovieCard,
  }
}
</script>
