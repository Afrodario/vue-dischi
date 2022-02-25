<template>
  <main>
    <div class="container">
      <div class="row row-cols-5 g-4">
        <div
              v-for="(disc, index) in filteredDiscs"
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
    props: {
      selectedGenre: String
    },

    data() {
        return {
            discList: [],
            selectedGenres: []
        }
    },

    computed: {
      filteredDiscs() {
        if (this.selectedGenre == "") {
          return this.discList;
        } else {
        return this.discList.filter(item => {
          return item.genre == this.selectedGenre;
        })
        } 
      }
    },

    methods: {
        getDiscList () {
            axios.get("https://flynn.boolean.careers/exercises/api/array/music")
            .then((response) => {
                this.discList = response.data.response;
                
                for (let i = 0; i < this.discList.length; i++) {
                  
                  if (!this.selectedGenres.includes(this.discList[i].genre)) {
                      this.selectedGenres.push(this.discList[i].genre);
                  }
                  
                }
                
                console.log("I generi selezionati sono:" + this.selectedGenres);
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

    .row {
      padding-bottom: 100px;
    }
}
</style>