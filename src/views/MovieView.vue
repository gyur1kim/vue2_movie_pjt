<template>
  <div class="movie">
    <h1>뀰movie</h1>
    <MovieCard 
      v-for="(movie, idx) in topMovies" :key="idx"
      :movie="movie"
    />
  </div>
</template>

<script>
import axios from 'axios'
import MovieCard from '@/components/MovieCard'

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
      const URL = 'https://api.themoviedb.org/3/movie/top_rated?api_key=2808f49cb7a157269d3c55874b8d52e5&language=ko-KR'

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
