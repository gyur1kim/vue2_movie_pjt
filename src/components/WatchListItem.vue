<template>
  <div class="watchListItem">
    <div 
      :class="{ click: movie.isClicked }" 
      @click="toggleClick">
      {{ movie.title }}</div>
  </div>
</template>

<script>
export default {
  name: 'WatchListItem',
  props: {
    movie: Object,
  },
  methods: {
    toggleClick() {
      this.$emit('toggle-click', this.movie)
    }
  }
}
</script>

<style>
.click {
  text-decoration: line-through;
  color: rgb(177, 177, 177);
}
.watchListItem div {
  cursor: pointer;
}
.watchListItem{
  width: 80%;
}

</style>