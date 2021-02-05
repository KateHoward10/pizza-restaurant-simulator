<template>
  <div class="oven-container">
    <div class="chimney" />
    <div class="main-oven" @click="putPizzaInOven">
      <div class="door">
        <div class="floor">
          <div
            v-for="(pizza, index) in pizzasInOven"
            :key="index"
            @click="removePizza(index)"
            class="space"
            :class="{'pizza': pizza !== null}"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Oven',
  props: {
    putPizzaInOven: Function,
    pizzasInOven: Array,
    removePizza: Function
  }
}
</script>

<style scoped>
.oven-container {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.chimney {
  height: 120px;
  width: 60px;
  background-color:#999;
}
.main-oven {
  height: 160px;
  width: 280px;
  border-top-left-radius: 50%;
  border-top-right-radius: 50%;
  margin-top: -5px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-end;
  background-color:#999;
}
.door {
  height: 100px;
  width: 180px;
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  border-top-left-radius: 50%;
  border-top-right-radius: 50%;
  border: 8px solid #888;
  border-bottom: none;
  background-color: #ff8c00;
}
.floor {
  height: 40px;
  width: 180px;
  background-color: #b45400;
  display: flex;
  flex-flow: row wrap;
}
.space {
  height: 10px;
  width: 80px;
  margin: 5px;
}
.pizza {
  background-color: #ffeebf;
  border-radius: 5px;
  cursor: pointer;
}
</style>
