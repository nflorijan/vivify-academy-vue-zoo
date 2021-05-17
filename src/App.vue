<template>
  <div id="app">
    <AnimalsList />
  </div>
</template>

<script>
import AnimalsList from './components/AnimalsList.vue'

export default {
  name: 'App',
  components: {
    AnimalsList
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
