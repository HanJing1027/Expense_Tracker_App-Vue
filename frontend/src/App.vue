<template>
  <Header />
  <section class="container">
    <Balabce :getBalabce="getBalabce" />
    <IncomeExpenses :getIncome="getIncome" :getExpenses="getExpenses" />
    <TransactionList :transactions="transactions" />
    <AddTransaction />
  </section>
</template>

<script setup>
import Header from './components/Header.vue'
import Balabce from './components/Balabce.vue'
import IncomeExpenses from './components/IncomeExpenses.vue'
import TransactionList from './components/TransactionList.vue'
import AddTransaction from './components/AddTransaction.vue'

import { computed, ref } from 'vue'

const transactions = ref([
  {
    id: 1,
    text: '月薪支入帳',
    amount: 500,
    category: 'plus',
  },
  {
    id: 2,
    text: '與公司同事聚餐',
    amount: 200,
    category: 'minus',
  },
])

const getIncome = computed(() => {
  return transactions.value
    .filter((item) => item.category === 'plus')
    .reduce((total, item) => total + item.amount, 0)
    .toFixed(2)
})

const getExpenses = computed(() => {
  return transactions.value
    .filter((item) => item.category === 'minus')
    .reduce((total, item) => total + item.amount, 0)
    .toFixed(2)
})

const getBalabce = computed(() => {
  const total = getIncome.value - getExpenses.value
  return total.toFixed(2)
})
</script>

<style scoped></style>
