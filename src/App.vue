<template>
  <div id="app">
    <DiscHeader/>
    <DiscMain @genresReady="getGenresList"/>
  </div>
</template>

<script>
import DiscHeader from './components/DiscHeader.vue';
import DiscMain from './components/DiscMain.vue';

export default {
  name: 'App',
  components: {
    DiscHeader,
    DiscMain
  },
  data () {
    return {
      capturedGenres: []
    }
  },
  methods: {
    getGenresList(searchGenres) {
      console.log("Arriva:" + searchGenres)
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Courier New', Courier, monospace;
}
</style>
