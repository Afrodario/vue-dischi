<template>
  <main>
    <div class="container">
      <div class="row row-cols-5 g-4">
        <div
              v-for="(disc, index) in discList.response"
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
            discList: []
        }
    },

    methods: {
        getDiscList () {
            axios.get("https://flynn.boolean.careers/exercises/api/array/music")
            .then((response) => {
                this.discList = response.data;
                console.log(response);
            })
        }
    },

    created() {
        this.getDiscList()
    }
}
</script>

<style scoped lang="scss">
main {
    background-color: #1e2d3b;
}
</style>