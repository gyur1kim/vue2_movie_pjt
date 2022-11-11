<template>
  <div class="watchListForm">
    <h1>보고싶은 영화는?</h1>
    <form @submit.prevent="createMovie">
      <input 
        v-model="inputMovie"
        type="text">
      <input type="submit">
    </form>
  </div>
</template>

<script>


export default {
  name: "WatchListForm",
  data(){
    return{
      inputMovie: null,
    }
  },
  methods: {
    createMovie(){
      if(this.inputMovie.trim()){
        this.$emit('create-movie', this.inputMovie)
      }
      this.inputMovie = null;
    }
  }
}
</script>

<style>
.watchListForm{
  padding-bottom: 60px;
}
</style>