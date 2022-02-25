<template>
  <header>
      <img class="float-start p-1"
      src="https://upload.wikimedia.org/wikipedia/commons/7/75/Spotify_icon.png">
      <select> 
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
        filteredArray: []
      }
    },
    props: ["genre"],
    methods: {
      genreFilter() {
        this.filteredArray = this.genre.filter(object => {
          return object.includes(this.item.value);
        })
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
}
</style>