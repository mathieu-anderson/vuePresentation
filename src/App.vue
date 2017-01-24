<template>
  <div id="app">
    <h1 v-on:click="reload()">tasteFight</h1>
      <searchMovie></searchMovie>
  </div>
</template>

<script>
import searchMovie from './components/searchMovie'

export default {
  name: 'app',
  components: {
    searchMovie
  }
}
</script>

<style>

img {
  max-width: 35vw;
  min-width: 200px;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
