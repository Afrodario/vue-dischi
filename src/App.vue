<template>
  <div id="app">
    <DiscHeader :genre="capturedGenres"
                @changedGenre="startSearch"/>
    <DiscMain @genresReady="getGenresList"
              />
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
    startSearch(valueTransmitted) {
      console.log("Ho ricevuto:" + valueTransmitted)
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Courier New', Courier, monospace;
}
</style>
