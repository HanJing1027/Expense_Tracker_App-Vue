<template>
  <Header />
  <main class="container">
    <Balabce :getBalabce="getBalabce" />
    <IncomeExpenses :getIncome="getIncome" :getExpenses="getExpenses" />
    <TransactionList @deleteTransaction="handleTransaction" :transactions="transactions" />
    <AddTransaction @addTransaction="handleAddTransaction" />
  </main>
</template>

<script setup>
import Header from './components/Header.vue'
import Balabce from './components/Balabce.vue'
import IncomeExpenses from './components/IncomeExpenses.vue'
import TransactionList from './components/TransactionList.vue'
import AddTransaction from './components/AddTransaction.vue'

import { computed, onMounted, ref, watch } from 'vue'

const transactions = ref([])

watch(
  transactions,
  () => {
    saveTransactionsToLocalStorage()
  },
  { deep: true }
)

onMounted(() => {
  const savedTransactions = JSON.parse(localStorage.getItem('transactions'))
  if (savedTransactions) {
    transactions.value = savedTransactions
  }
})

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

const handleAddTransaction = (transactionData) => {
  transactions.value.push(transactionData)
}

const handleTransaction = (transaction) => {
  const index = transactions.value.findIndex((item) => item.id === transaction.id)
  if (index !== -1) {
    transactions.value.splice(index, 1)
  }
}

const saveTransactionsToLocalStorage = () => {
  localStorage.setItem('transactions', JSON.stringify(transactions.value))
}
</script>

<style scoped></style>
