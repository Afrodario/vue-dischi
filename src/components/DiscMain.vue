<template>
  <main>
    <!-- <button @click="$emit('pippo', selectedGenres)">PROVA</button> -->
    <div class="container">
      <div class="row row-cols-5 g-4">
        <div
              v-for="(disc, index) in discList"
              :key="index">
              <DiscCard :disc="disc"/>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
// Integrazione di AXIOS
const axios = require("axios");
import DiscCard from './partials/DiscCard.vue';
export default {
    name: "DiscMain",
    components: {
      DiscCard,
    },

    data() {
        return {
            discList: [],
            allGenres: [],
            selectedGenres: []
        }
    },

    methods: {
        getDiscList () {
            axios.get("https://flynn.boolean.careers/exercises/api/array/music")
            .then((response) => {
                this.discList = response.data.response;
                
                for (let i = 0; i < this.discList.length; i++) {
                  
                  this.allGenres.push(this.discList[i].genre);
                }
                
                this.selectedGenres.push([...new Set(this.allGenres)]);
                console.log(this.selectedGenres);
            })
        },
        emitSelectedGenres() {
          this.$emit("genresReady", this.selectedGenres);
        }
    },

    created() {
        this.getDiscList();
        this.emitSelectedGenres()
    }
}
</script>

<style scoped lang="scss">
main {
    background-color: #1e2d3b;
}
</style>