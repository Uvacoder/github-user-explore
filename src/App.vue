<template>
  <div id="app">
    <Explore />
  </div>
</template>

<script>
import Explore from './components/Explore.vue'

export default {
  name: 'App',
  components: {
    Explore
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
