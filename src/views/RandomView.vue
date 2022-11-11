<template>
  <div>
    <h1>뀰random</h1>
    <button 
      @click="recommendMovie"
    >
      영화 chu 1000
    </button>
    <img :src="recommendMoviePosterPath" alt="">
    <div>{{ movie.title }}</div>
  </div>
</template>

<script>
import axios from 'axios'
import api_key from '../key.js'

const _ = require('lodash')
const MOVIE_API = api_key

export default {
  name: 'RandomView',
  data() {
    return {
      highMovies: [],
      movie: null,
      recommendMoviePosterPath: null,
    }
  },
  methods: {
    highRatedMovies() {
      const URL = `https://api.themoviedb.org/3/movie/top_rated?api_key=${MOVIE_API}&language=ko-KR`

      axios({
        method: 'GET',
        url: URL
      })
        .then((response) => {
          this.highMovies = response.data.results
          this.recommendMovie();
        })
        .catch((error) => {
          console.log(error);
        })
    },
    recommendMovie(){
      let movie = _.sample(this.highMovies);
      while(this.movie && movie.id === this.movie.id){
        movie = _.sample(this.highMovies);
      }
      this.movie = movie
      this.recommendMoviePosterPath = `https://www.themoviedb.org/t/p/w300_and_h450_bestv2/${movie.poster_path}`
    }
  },
  created(){
    this.highRatedMovies()
  }
}
</script>

<style>

</style>
