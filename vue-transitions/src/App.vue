<template>
  <div id="app">
    <transitionDemo />
  </div>
</template>

<script>
import transitionDemo from './components/transitionDemo'

export default {
  name: 'app',
  components: {
    transitionDemo
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
