<template>
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
import { ref, onMounted } from 'vue'
import { menu } from '../data.js'

export default {
  name: 'Orders',
  props: {
    newBase: Function,
  },
  setup() {
    const orders = ref([]);

    function generateOrder() {
      const number = (Math.random() * 3 | 0) + 1;
      const order = [];
      for (let i = 0; i < number; i++) {
        order.push(menu[Math.random() * menu.length | 0].name);
      }
      return order;
    }

    onMounted(() => {
      setInterval(() => orders.value.push(generateOrder()), 2000);
    })

    return { orders };
  }
}
</script>

<style scoped>
.order-container {
  width: 100%;
  z-index: 5;
  display: flex;
  flex-direction: row-reverse;
  align-items: flex-start;
  justify-content: flex-start;
  position: absolute;
  left: 0;
  right: 0;
}
.order {
  background-color: #fa9f28;
  margin: 8px;
  min-width: 90px;
  font-size: 14px;
}
</style>
