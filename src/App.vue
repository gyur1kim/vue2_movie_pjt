<template>
  <div id="app">
    <nav>
      <router-link :to="{ name: 'movie' }">Movie</router-link> |
      <router-link :to="{ name: 'random'}">Random</router-link> |
      <router-link :to="{ name: 'watch-list'}">WatchList</router-link>
    </nav>
    <router-view  class="container"/>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
  background-color: #dbf3e8;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
