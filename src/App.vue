<template>
  <div id="app">
    <ImageScroller />
  </div>
</template>

<script>
import ImageScroller from './components/ImageScroller.vue'

export default {
  name: 'App',
  components: {
    ImageScroller
  }
}
</script>

<style lang="scss">
html,
body {
  margin: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0;
}
</style>
