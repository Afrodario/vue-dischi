<template>
  <main>
    <div class="container">
      <div class="row row-cols-5">
        <DiscCard v-for="(disc, index) in discList.response"
            :key="index"
            :disc="disc"/>
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

</style>