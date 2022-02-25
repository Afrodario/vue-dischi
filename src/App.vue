<template>
  <div id="app">
    <DiscHeader :genre="capturedGenres"
                @changedGenre="startSearch"/>
    <DiscMain @genresReady="getGenresList"
              :selectedGenre="selectedGenre"/>
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
      capturedGenres: [],
      selectedGenre: ""
    }
  },
  methods: {
    getGenresList(searchGenres) {
      console.log(searchGenres);
        this.capturedGenres = searchGenres;
        console.log(this.capturedGenres)
    },
    startSearch(valueTransmitted) {
      console.log("Ho ricevuto:" + valueTransmitted);
      this.selectedGenre = valueTransmitted;
      console.log("Ho assegnato ad una variabile il valore trasmesso " + this.selectedGenre)
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Courier New', Courier, monospace;
  margin-top: -25px;
}
</style>
