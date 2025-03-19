<template>
  <Header />
  <section class="container">
    <Balabce />
    <IncomeExpenses />
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

import { ref } from 'vue'

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
</script>

<style scoped></style>
