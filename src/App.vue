<template>
  <div id="app">
    <DiscHeader :genre="capturedGenres"/>
    <DiscMain @genresReady="getGenresList"
              @changedGenre="startSearch"/>
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
      capturedGenres: ""
    }
  },
  methods: {
    getGenresList(searchGenres) {
      console.log(searchGenres);
        this.capturedGenres = searchGenres;
        console.log(this.capturedGenres)
    },
    startSearch() {
      alert("PROVA")
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Courier New', Courier, monospace;
}
</style>
