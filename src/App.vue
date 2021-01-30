<template>
  <Oven />
  <Surface />
</template>

<script>
import Oven from './components/Oven.vue'
import Surface from './components/Surface.vue'

export default {
  name: 'App',
  components: {
    Oven,
    Surface
  }
}
</script>

<style>
body {
  margin: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-color: #FEE2BF;
  display: flex;
  flex-direction: column;
  align-items: center;
  min-height: 100vh;
}
</style>
