<template>
  <div id="app">
    <h1>A Vue.js demo</h1>
      <componentDemo />
  </div>
</template>

<script>
  import componentDemo from './components/componentDemo'
  export default {
    name: 'app',
    components: {
      componentDemo
    }
  }
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>
