<template>
  <div class="movie">
    <div class="row row-cols-1 row-cols-md-3 g-4">
      <MovieCard 
        v-for="movie in topMovies" :key="movie.id"
        :movie="movie"
      />
    </div>
  </div>
</template>


<script>
import axios from 'axios'
import api_key from '../key.js'
import MovieCard from '@/components/MovieCard'

const MOVIE_API = api_key;

export default {
  name: 'MovieView',
  data() {
    return{
      topMovies: null,
    }
  },
  components: {
    MovieCard,
  },
  methods: {
    topRatedMovies(){
      const URL = `https://api.themoviedb.org/3/movie/top_rated?api_key=${MOVIE_API}&language=ko-KR`

      axios({
        method: 'GET',
        url: URL,
      })
        .then((response)=>{
          // console.log(response);
          // console.log(response.data.results);
          this.topMovies = response.data.results;
        })
        .catch((error)=>{
          console.log(error);
        })
    },
  },
  created(){
    this.topRatedMovies();
  }
}
</script>

<style>
.movie {
  margin-top: 60px;
  margin-bottom: 60px;
}
</style>