<template>
  <Controls :newBase="newBase" />
  <Oven />
  <Surface :currentPizza="currentPizza" :selected="selected" :selectIngredient="selectIngredient" />
</template>

<script>
import { ref } from 'vue'
import Oven from './components/Oven.vue'
import Surface from './components/Surface.vue'
import Controls from './components/Controls.vue'

export default {
  name: 'App',
  setup() {
    const currentPizza = ref(null);
    const selected = ref(null);

    function newBase() {
      currentPizza.value = [];
    }

    function selectIngredient(index) {
      selected.value = index;
    }

    return { currentPizza, newBase, selected, selectIngredient };
  },
  components: {
    Controls,
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
