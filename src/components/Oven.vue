<template>
  <div class="container">
    <div class="chimney" />
    <div class="main-oven">
      <div class="door">
        <div class="floor" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Oven'
}
</script>

<style scoped>
.container {
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
}
</style>
