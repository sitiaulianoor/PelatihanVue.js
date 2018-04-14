<template>
  <div id="app">
    <img src="./assets/logo.png">
    <star-wars />
  </div>
</template>

<script>
  import StarWars from './components/StarWars'

export default {
  name: 'app',
  components: {
    StarWars
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
