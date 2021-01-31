<template>
  <div class="rod" />
  <div class="order-container">
    <div
      v-for="(order, index) in orders"
      :key="index"
      class="order"
    >
      <p
        v-for="(item, index) in order"
        :key="index"
      >
        1 ✕ {{ item }}
      </p>
    </div>
  </div>
</template>

<script>
import { menu } from '../data.js'

export default {
  name: 'Orders',
  props: {
    newBase: Function
  },
  setup() {
    function generateOrder() {
      const number = (Math.random() * 3 | 0) + 1;
      const order = [];
      for (let i = 0; i < number; i++) {
        order.push(menu[Math.random() * menu.length | 0].name);
      }
      return order;
    }

    const orders = [generateOrder(), generateOrder(), generateOrder()];

    return { orders };
  }
}
</script>

<style scoped>
.rod {
  width: 100%;
  height: 8px;
  background-color: #ddd;
}
.order-container {
  width: 100%;
  z-index: 5;
  display: flex;
  flex-direction: row;
  align-items: flex-start;
  justify-content: flex-end;
  position: absolute;
  left: 0;
  right: 0;
}
.order {
  background-color: #fa9f28;
  margin: 10px;
  min-width: 90px;
  font-size: 14px;
}
</style>
