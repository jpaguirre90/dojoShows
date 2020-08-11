<template>
  <div id="app">
    <h3>Dojo Shows</h3>
    <dojoShows/>
  </div>
</template>

<script>

import dojoShows from './components/dojoShows.vue'

export default {
  name: 'App',
  data(){
    return{
      shows:[]
    }
  },
  components: {
    dojoShows
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
