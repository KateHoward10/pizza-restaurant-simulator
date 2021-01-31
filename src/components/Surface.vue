<template>
  <div class="surface">
    <div class="pizza-container">
      <div class="pizza" v-if="currentPizza !== null" />
    </div>
    <div class="ingredients">
      <div
        v-for="(ingredient, index) in ingredients"
        :key="index"
        class="pot"
      >
        {{ ingredient.icon }}
      </div>
    </div>
  </div>
</template>

<script>
import { ingredients } from '../data.js'

export default {
  name: 'Surface',
  setup() {
    return { ingredients };
  },
  props: {
    currentPizza: Array
  }
}
</script>

<style scoped>
.surface {
  background-color: #ddd;
  width: 100%;
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
.ingredients {
  width: 100%;
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  padding-bottom: 8px;
}
.pot {
  border: 2px solid #666;
  border-top: none;
  border-bottom-left-radius: 10px;
  border-bottom-right-radius: 10px;
  padding: 6px;
  min-width: 30px;
  margin: 5px;
  font-size: 20px;
}
.pizza-container {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 40px;
}
.pizza {
  height: 180px;
  width: 280px;
  border-radius: 50%;
  background-color: #ffeebf;
}
</style>
