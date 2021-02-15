<template>
  <div class="order-container">
    <div
      v-for="(order, index) in orders"
      :key="index"
      class="order"
    >
      <p
        v-for="({ item, quantity }, index) in formatOrder(order)"
        :key="index"
      >
        {{ quantity }} ✕ {{ item }}
      </p>
    </div>
  </div>
</template>

<script>
import { onMounted } from 'vue'

export default {
  name: 'Orders',
  props: {
    newBase: Function,
    orders: Array,
    interval: Number,
    startAddingOrders: Function
  },
  setup(props) {
    function formatOrder(order) {
      const smOrder = [...new Set(order)];
      return smOrder.map(pizza => {
        return { item: pizza, quantity: order.filter(p => p === pizza).length };
      });
    }

    onMounted(() => props.startAddingOrders());

    return { formatOrder };
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
