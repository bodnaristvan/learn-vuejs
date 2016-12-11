<template>
  <div id="app">
    <navbar></navbar>
    <featurelist></featurelist>
  </div>
</template>

<script>
import FeatureList from './components/FeatureList'
import Navbar from './components/Navbar'

export default {
  name: 'app',
  components: {
    Navbar,
    'featurelist': FeatureList
  }
}
</script>

<style>
body {
  margin: 0;
  padding: 0;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
