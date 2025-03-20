<template>
  <div class="inc-exp-box">
    <div>
      <h4>收入</h4>
      <p class="money plus">+${{ getIncome }}</p>
    </div>
    <div>
      <h4>支出</h4>
      <p class="money minus">-${{ getExpenses }}</p>
    </div>
  </div>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
  transactions: {
    type: Array,
    default: () => [],
  },
})

const getIncome = computed(() => {
  return props.transactions
    .filter((item) => item.category === 'plus')
    .reduce((acc, item) => acc + item.amount, 0)
    .toFixed(2)
})

const getExpenses = computed(() => {
  return props.transactions
    .filter((item) => item.category === 'minus')
    .reduce((acc, item) => acc + item.amount, 0)
    .toFixed(2)
})
</script>

<style lang="scss" scoped>
.inc-exp-box {
  display: flex;
  justify-content: space-between;
  background-color: #fff;
  padding: 25px 50px;
  border-radius: 5px;
  box-shadow: 0 5px 5px 1px #00000016;

  div {
    flex: 1;
    text-align: center;
    &:first-child {
      border-right: 1px solid #ccc;
    }

    h4 {
      font-size: 1.125rem;
      color: #333;
    }

    .money {
      font-size: 1.3rem;
      margin-top: 10px;

      &.plus {
        color: #4caf50;
      }

      &.minus {
        color: #dc5555;
      }
    }
  }
}
</style>
