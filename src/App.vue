<template>
  <div id="app">
    <DiscHeader/>
    <DiscMain/>
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
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Courier New', Courier, monospace;
}
</style>
