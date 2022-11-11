<template>
  <div class="random d-flex flex-column align-items-center">
    <button 
      @click="recommendMovie"
      class="btn"
    >
      다른 영화를 추천받고싶어요!
    </button>

    <div class="card" style="width: 18rem;">
      <img :src="recommendMoviePosterPath" class="card-img-top" alt="...">
      <div class="card-body">
        <p class="card-title fw-bold">{{ movie.title }}</p>
      </div>
    </div>

    <img  alt="">
    <div></div>
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
    },
  },
  created(){
    this.highRatedMovies()
  }
}
</script>

<style>
.random {
  margin-top: 60px;
  margin-bottom: 60px;
}
.btn {
  width: 70%;
  height: 50px;
  background-color: #42b983;
  color: white;
}
.random .card{
  margin-top: 60px;
}
</style>
