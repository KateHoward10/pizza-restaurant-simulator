<template>
  <div class="pizza" @click="addTopping">
    <div
      v-for="(ingredient, index) in currentPizza"
      :key="index"
      class="layer"
      :class="ingredients[index].name"
    />
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
    currentPizza: Array,
    addTopping: Function
  }
}
</script>

<style scoped>
.pizza {
  height: 200px;
  width: 300px;
  border-top-left-radius: 50%;
  border-top-right-radius: 50%;
  border-bottom-left-radius: 45%;
  border-bottom-right-radius: 45%;
  background-color: #ffeebf;
  position: relative;
}
.layer {
  height: 160px;
  width: 260px;
  border-top-left-radius: 50%;
  border-top-right-radius: 50%;
  border-bottom-left-radius: 45%;
  border-bottom-right-radius: 45%;
  position: absolute;
  margin: 20px;
}
.tomato {
  background-color:#cc3a27;
}
.mozzarella {
  background-image: radial-gradient(#feffc9 40%, transparent 40%),
    radial-gradient(#feffc9 40%, transparent 40%);
  background-size: 80px 80px;
  background-position: 0 0, 50px 50px;
}
.olives {
  background-image: radial-gradient(#222 16%, transparent 18%),
  radial-gradient(#222 16%, transparent 18%);
  background-size: 60px 60px;
  background-position: 0 0, 20px 20px;
}
.mushrooms {
  background-image: radial-gradient(#ddd 21%, transparent 24%),
  radial-gradient(#ddd 21%, transparent 24%);
  background-size: 50px 50px;
  background-position: 0 0, 20px 20px;
}
</style>
