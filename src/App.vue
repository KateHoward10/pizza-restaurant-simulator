<template>
  <Controls
    :start="start"
    :time="time"
    :playing="playing"
    :newBase="newBase"
  />
  <Orders />
  <Oven :putPizzaInOven="putPizzaInOven" />
  <Surface
    :currentPizza="currentPizza"
    :selected="selected"
    :selectIngredient="selectIngredient"
    :addTopping="addTopping"
  />
</template>

<script>
import { ref } from 'vue'
import Controls from './components/Controls.vue'
import Orders from './components/Orders.vue'
import Oven from './components/Oven.vue'
import Surface from './components/Surface.vue'

export default {
  name: 'App',
  setup() {
    const currentPizza = ref(null);
    const selected = ref(null);
    const pizzasInOven = ref([]);
    const time = ref(1080);
    const playing = ref(false);

    function newBase() {
      currentPizza.value = [];
    }

    function selectIngredient(index) {
      selected.value = index;
    }

    function addTopping() {
      if (currentPizza.value !== null && selected.value !== null) {
        currentPizza.value.push(selected.value);
      }
    }

    function putPizzaInOven() {
      if (currentPizza.value !== null) {
        pizzasInOven.value.push({
          toppings: currentPizza.value,
          timeInOven: 0
        });
        setInterval(() => {
          pizzasInOven.value[pizzasInOven.value.length - 1].timeInOven++;
        }, 1000);
        currentPizza.value = null;
      }
    }

    function start() {
      playing.value = true;
      setInterval(() => {
        time.value < 1320 ? time.value++ : playing.value = false;
      }, 1000);
    }

    return {
      currentPizza,
      newBase,
      selected,
      selectIngredient,
      addTopping,
      putPizzaInOven,
      start,
      time,
      playing
    };
  },
  components: {
    Orders,
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
