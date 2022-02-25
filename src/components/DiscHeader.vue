<template>
  <header class="d-flex justify-content-between align-items-center">
      <img class="float-start p-1"
      src="https://upload.wikimedia.org/wikipedia/commons/7/75/Spotify_icon.png">
      
      <!-- La soluzione più semplice è legare un v-model ad option e riversarlo
      in una variabile vuota in data, poi lanciare la emit direttamente al change
      senza ricorrere a metodi-->
      <select v-model="targetGenre"
      @change="getValue(targetGenre)"> 
        <option value="">Tutti i generi</option>
        <option
            v-for="(item, index) in genre"
            :key="index"
            :value="item">
            {{item}}
            </option>
      </select>
  </header>
</template>

<script>
export default {
    name: "DiscHeader",

    data() {
      return {
        targetGenre: ""
      }
    },

    props: {
      "genre": Array
      },

    methods: {
      getValue() {
          this.$emit("changedGenre", this.targetGenre);
        }
      }
    }
</script>

<style scoped lang="scss">
header {
  background-color: #2e3a46;
  height: 100px;

  img {
    height: 50px;
  }

  select {
    margin-right: 20px;
    font-size: 20px;
    font-family: sans-serif;
    padding: 10px;
  }
}
</style>