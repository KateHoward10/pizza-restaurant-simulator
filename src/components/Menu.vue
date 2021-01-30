<template>
  <ul>
    <li v-for="(pizza, index) in menu" :key="index">
      <span class="name">{{ pizza.name }}</span>
      {{ pizza.description }}
    </li>
  </ul>
</template>

<script>
import { data } from '../data.js'

export default {
  name: 'Menu',
  setup() {
    const menu = data.menu.map(pizza => {
      const description = pizza.ingredients.map(ingredient => data.ingredients[ingredient].name).join(", ");
      return {
        ...pizza,
        description
      }
    });
    return { menu };
  }
}
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 8px;
  max-width: 240px;
  position: absolute;
  top: 0;
  left: 0;
  background-color: #eee;
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
