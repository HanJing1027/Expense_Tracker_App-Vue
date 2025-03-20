<template>
  <div class="balabce-box">
    <h4>YOUR BALABCE</h4>
    <h1 class="balabce">${{ getBalabce }}</h1>
  </div>
</template>

<script setup>
const props = defineProps({
  getBalabce: {
    type: Number,
    default: 0,
  },
})
</script>

<style lang="scss" scoped>
.balabce-box {
  margin: 25px 0;

  h4 {
    font-size: 1.125rem;
    color: #444;
  }
  h1 {
    font-size: 2.125rem;
    color: #333;
  }
}
</style>
