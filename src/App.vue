<template>
  <div id="app">
    <directive></directive>
    <transition-app></transition-app>
  </div>
</template>

<script>
import directive from './components/directive'
import transitionApp from './components/transition'
export default {
  components: {
    directive,
    transitionApp
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
