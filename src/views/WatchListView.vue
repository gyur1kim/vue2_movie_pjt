<template>
  <div class="watchList d-flex flex-column align-items-center">
    <WatchListForm @create-movie="createMovie" />
    <WatchListItem 
      v-for="(movie, idx) in favoriteMovies" :key="idx" 
      :movie="movie"
      @toggle-click="toggleClick"
    />
  </div>
</template>

<script>
import WatchListForm from '@/components/WatchListForm';
import WatchListItem from '@/components/WatchListItem';

export default {
  name: 'WatchListView',
  data(){
    return{
      favoriteMovies: [],
    }
  },
  components: {
    WatchListForm,
    WatchListItem,
  },
  methods: {
    createMovie(movie){
      const movieItem = {
        title: movie,
        isClicked: false,
      }
      this.favoriteMovies.push(movieItem);
      console.log(this.favoriteMovies);
    },
    toggleClick(favMovie) {
      for (const movie of this.favoriteMovies){
        if (movie === favMovie) {
          movie.isClicked = !movie.isClicked;
          break;
        }
      }
    }
  }
}
</script>

<style>
.watchList{
  margin-top: 60px;
  margin-bottom: 60px;
}
.watchListItem:nth-child(even){
  padding: 10px;
  background-color: rgb(250, 250, 250);
}
.watchListItem:nth-child(odd){
  padding: 10px;
  background-color: rgb(240, 240, 240);
}
</style>