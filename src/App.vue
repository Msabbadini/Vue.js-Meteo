<template>
  <div id="app">
    <meteo></meteo>
  </div>
</template>

<script>
import Meteo from './components/Meteo.vue'

export default {
  name: 'App',
  components: {
    'meteo': Meteo
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
