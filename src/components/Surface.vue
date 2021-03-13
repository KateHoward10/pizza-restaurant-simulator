<template>
  <div class="surface">
    <div class="pizza-container">
      <Pizza
        v-if="currentPizza !== null"
        :currentPizza="currentPizza"
        :addTopping="addTopping"
      />
      <div v-if="currentPizza === null">
        <div v-for="(box, index) in boxedPizzas" :key="index" class="box" />
      </div>
      <div v-if="message" class="message">{{ message }}<button @click="clearMessage">Continue</button></div>
    </div>
    <div class="ingredients">
      <div
        v-for="(ingredient, index) in ingredients"
        :key="index"
        @click="selectIngredient(index)"
        class="pot"
        :class="{ selected: selected === index }"
      >
        {{ ingredient.icon }}
      </div>
    </div>
    <div class="boxes" @click="boxPizza">
      <div v-for="index in [0,1,2,3]" :key="index" class="box" />
    </div>
  </div>
</template>

<script>
import { ingredients } from '../data.js'
import Pizza from './Pizza.vue'

export default {
  name: 'Surface',
  props: {
    currentPizza: Array,
    selected: Number,
    selectIngredient: Function,
    addTopping: Function,
    boxedPizzas: Array,
    boxPizza: Function,
    message: String,
    clearMessage: Function
  },
  setup() {
    return { ingredients };
  },
  components: {
    Pizza
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
  position: relative;
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
  cursor: pointer;
}
.selected {
  transform: scale(1.2);
  border-color: #333;
}
.pizza-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 40px;
}
.boxes {
  position: absolute;
  top: 0;
  right: 0;
  display: flex;
  flex-direction: column;
}
.box {
  width: 180px;
  height: 20px;
  border: 1px solid #ddd;
  background-color: #fff;
}
.message {
  background-color: #eee;
  padding: 2px;
  margin: 5px;
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
