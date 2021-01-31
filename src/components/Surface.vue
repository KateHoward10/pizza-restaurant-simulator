<template>
  <div class="container">
    <div class="pizza" v-if="currentPizza !== null" />
  </div>
</template>

<script>
export default {
  name: 'Surface',
  props: {
    currentPizza: Array
  }
}
</script>

<style scoped>
.container {
  background-color: #ddd;
  width: 100%;
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: center;
}
.pizza {
  height: 180px;
  width: 280px;
  border-radius: 50%;
  background-color: #ffeebf;
}
</style>
