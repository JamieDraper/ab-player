<template>
  <div id="app">
    <ABPlayer/>
    <ABPlayer/>
  </div>
</template>

<script>
import ABPlayer from './components/ABPlayer.vue'

export default {
  name: 'app',
  components: {
    ABPlayer
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
