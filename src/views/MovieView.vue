<template>
  <div class="movie">
    <h1>뀰movie</h1>
    <MovieCard 
      v-for="movie in topMovies" :key="movie.id"
      :movie="movie"
    />
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
