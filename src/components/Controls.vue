<template>
  <div class="controls">
    <button @click="newBase">New base</button>
    <button @click="menuOpen = true">Menu</button>
    <div v-if="menuOpen" class="container">
      <button @click="menuOpen = false" class="close-button">✕</button>
      <ul>
        <li v-for="(pizza, index) in list" :key="index">
          <span class="name">{{ pizza.name }}</span>
          {{ pizza.description }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue'
import { ingredients, menu } from '../data.js'

export default {
  name: 'Controls',
  props: {
    newBase: Function
  },
  setup() {
    const list = menu.map(pizza => {
      const description = pizza.ingredients.map(ingredient => ingredients[ingredient].name).join(", ");
      return {
        ...pizza,
        description
      }
    });
    const menuOpen = ref(false);
    return { list, menuOpen };
  }
}
</script>

<style scoped>
.controls {
  position: absolute;
  top: 0;
  left: 0;
  padding: 8px;
  text-align: left;
}
button {
  display: block;
  margin: 4px;
}
.container {
  max-width: 240px;
  background-color: #eee;
  position: relative;
}
.close-button {
  position: absolute;
  top: 0;
  right: 0;
  border: none;
  background-color: transparent;
  margin: 2px;
}
ul {
  list-style: none;
  margin: 0;
  padding: 8px;
}
li {
  margin-bottom: 12px;
  text-align: left;
}
.name {
  font-weight: bold;
  margin-right: 6px;
}
</style>
