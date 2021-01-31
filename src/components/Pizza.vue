<template>
  <div class="pizza" @click="addTopping">
    <div
      v-for="(ingredient, index) in currentPizza"
      :key="index"
      class="layer"
      :class="ingredients[ingredient].name.replace(' ', '-').replace('’', '')"
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
  background-image: radial-gradient(#222 12%, transparent 14%),
  radial-gradient(#222 12%, transparent 14%);
  background-size: 60px 60px;
  background-position: 0 0, 20px 20px;
}
.mushrooms {
  background-image: radial-gradient(#ddd 21%, transparent 24%),
  radial-gradient(#ddd 21%, transparent 24%);
  background-size: 50px 50px;
  background-position: 0 0, 20px 20px;
}
.onions {
  background-image: radial-gradient(#fad184 16%, transparent 18%),
  radial-gradient(#fad184 16%, transparent 18%);
  background-size: 50px 50px;
  background-position: 0 0, 20px 20px;
}
.peppers {
  background-image: radial-gradient(#f00 10%, transparent 11%),
  radial-gradient(#f00 10%, transparent 11%);
  background-size: 80px 80px;
  background-position: 0 0, 20px 20px;
}
.sweetcorn {
  background-image: radial-gradient(#ff0 10%, transparent 11%),
  radial-gradient(#ff0 10%, transparent 11%);
  background-size: 14px 14px;
  background-position: 0 0, 20px 20px;
}
.aubergine {
  background-image: radial-gradient(#faf38c 14%, transparent 16%),
  radial-gradient(#faf38c 14%, transparent 16%);
  background-size: 40px 40px;
  background-position: 0 0, 24px 24px;
}
.avocado {
  background-image: radial-gradient(#58ed6c 20%, transparent 24%),
  radial-gradient(#58ed6c 20%, transparent 24%);
  background-size: 60px 60px;
  background-position: 0 0, 24px 42px;
}
.sweet-potato {
  background-image: radial-gradient(#f5a545 26%, transparent 30%),
  radial-gradient(#f5a545 26%, transparent 30%);
  background-size: 70px 70px;
  background-position: 0 0, 36px 36px;
}
.goats-cheese {
  background-image: radial-gradient(#eee 18%, transparent 22%),
  radial-gradient(#eee 18%, transparent 22%);
  background-size: 50px 50px;
  background-position: 0 0, 13px 17px;
}
.chicken {
  background-image: radial-gradient(#fad09d 21%, transparent 23%),
  radial-gradient(#fad09d 21%, transparent 23%);
  background-size: 54px 54px;
  background-position: 0 0, 23px 45px;
}
.bacon {
  background-image: radial-gradient(#b8445b 25%, transparent 26%),
  radial-gradient(#b8445b 25%, transparent 26%);
  background-size: 27px 27px;
  background-position: 0 0, 17px 22px;
}
.meat {
  background-image: radial-gradient(#94232d 13%, transparent 15%),
  radial-gradient(#94232d 13%, transparent 15%);
  background-size: 50px 50px;
  background-position: 0 0, 42px 42px;
}
.tuna {
  background-image: radial-gradient(#f5c4c8 20%, transparent 24%),
  radial-gradient(#f5c4c8 24%, transparent 20%);
  background-size: 42px 42px;
  background-position: 0 0, 17px 17px;
}
</style>
