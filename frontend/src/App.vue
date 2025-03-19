<template>
  <Header />
  <section class="container">
    <Balabce />
    <IncomeExpenses />
    <TransactionList />
    <AddTransaction />
  </section>
</template>

<script setup>
import Header from './components/Header.vue'
import Balabce from './components/Balabce.vue'
import IncomeExpenses from './components/IncomeExpenses.vue'
import TransactionList from './components/TransactionList.vue'
import AddTransaction from './components/AddTransaction.vue'
</script>

<style scoped></style>
