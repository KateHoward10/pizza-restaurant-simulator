<template>
  <div class="rod" />
  <Controls
    :start="start"
    :time="time"
    :playing="playing"
    :newBase="newBase"
  />
  <Orders
    v-if="playing"
    :orders="orders"
    :interval="interval"
    :startAddingOrders="startAddingOrders"
  />
  <Oven
    :putPizzaInOven="putPizzaInOven"
    :pizzasInOven="pizzasInOven"
    :removePizza="removePizza"
  />
  <Surface
    :currentPizza="currentPizza"
    :selected="selected"
    :selectIngredient="selectIngredient"
    :addTopping="addTopping"
    :boxedPizzas="boxedPizzas"
    :boxPizza="boxPizza"
  />
</template>

<script>
import { ref } from 'vue'
import Controls from './components/Controls.vue'
import Orders from './components/Orders.vue'
import Oven from './components/Oven.vue'
import Surface from './components/Surface.vue'
import { menu } from './data.js'

export default {
  name: 'App',
  setup() {
    const currentPizza = ref(null);
    const selected = ref(null);
    const pizzasInOven = ref([null,null,null,null]);
    const time = ref(1080);
    const playing = ref(false);
    const removedPizza = ref(null);
    const boxedPizzas = ref([]);
    const orders = ref([]);
    const interval = ref(5000);
    const selectedOrder = ref(null);

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
      if (currentPizza.value !== null && pizzasInOven.value.indexOf(null) > -1) {
        const pizzaIndex = pizzasInOven.value.indexOf(null);
        pizzasInOven.value[pizzaIndex] = {
          toppings: currentPizza.value,
          timeInOven: 0
        };
        setInterval(() => {
          if (pizzasInOven.value[pizzaIndex]) pizzasInOven.value[pizzaIndex].timeInOven++;
        }, 1000);
        currentPizza.value = null;
      }
    }

    function removePizza(index) {
      removedPizza.value = pizzasInOven.value[index];
      pizzasInOven.value[index] = null;
    }

    function boxPizza() {
      if (currentPizza.value === null && removedPizza.value !== null) {
        boxedPizzas.value.push(removedPizza.value);
      }
    }

    function generateOrder() {
      const number = (Math.random() * 3 | 0) + 1;
      const order = [];
      for (let i = 0; i < number; i++) {
        order.push(menu[Math.random() * menu.length | 0].name);
      }
      return order;
    }

    function startAddingOrders() {
      setInterval(() => {
        orders.value.push(generateOrder());
        interval.value = (Math.random() * 10000) + 10000;
      }, interval.value);
    }

    function selectOrder(index) {
      selectedOrder.value = orders[index];
    }

    function start() {
      playing.value = true;
      setInterval(() => {
        time.value < 1320 ? time.value++ : playing.value = false;
      }, 1000);
    }

    return {
      currentPizza,
      selected,
      pizzasInOven,
      newBase,
      orders,
      selectIngredient,
      addTopping,
      putPizzaInOven,
      removePizza,
      boxedPizzas,
      boxPizza,
      start,
      time,
      playing,
      startAddingOrders,
      selectOrder
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
.rod {
  width: 100%;
  height: 8px;
  background-color: #ddd;
}
</style>
