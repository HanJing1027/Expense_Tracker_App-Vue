<template>
  <div class="history-box">
    <h3>History</h3>
    <p v-if="transactions.length === 0" class="no-records">尚未有歷史紀錄</p>
    <ul v-else class="list">
      <li v-for="transaction in transactions" :key="transaction.id" :class="transaction.category">
        <span>{{ transaction.text }}</span>
        <span>{{ transaction.category === 'plus' ? '+' : '-' }} ${{ transaction.amount }}</span>
        <button @click="deleteTransaction(transaction)" class="delete-btn">x</button>
      </li>
    </ul>
  </div>
</template>

<script setup>
const props = defineProps({
  transactions: {
    type: Array,
    default: () => [],
  },
})

const emits = defineEmits(['deleteTransaction'])

const deleteTransaction = (transaction) => {
  emits('deleteTransaction', transaction)
}
</script>

<style lang="scss" scoped>
@import '../assets/styles/variables';

.history-box {
  margin: 2rem 0;
  width: 100%;

  h3 {
    @include subtitle;
  }

  .no-records {
    text-align: center;
    color: #888;
    font-style: italic;
    line-height: 3;
  }
}

.list {
  display: flex;
  flex-direction: column;
  gap: 0.625rem;
  width: 100%;
  margin: 1rem 0;

  li {
    position: relative;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0.9375rem 0.75rem;
    background-color: #fff;
    box-shadow: 0 0 5px 1px rgba(0, 0, 0, 0.09);
    border-radius: 5px;

    &::before {
      content: '';
      position: absolute;
      top: 0;
      left: -2rem;
      height: 100%;
      width: 2rem;
    }

    &.plus {
      border-right: 0.35rem solid #4caf50;
    }

    &.minus {
      border-right: 0.35rem solid #dc5555;
    }

    span {
      font-size: 1rem;
      color: #666;

      &:first-child {
        overflow: hidden;
        text-overflow: ellipsis;
        margin-right: 0.5rem;
        flex: 1;
      }

      &:last-of-type {
        font-weight: 500;
        white-space: nowrap;
      }
    }

    .delete-btn {
      cursor: pointer;
      position: absolute;
      left: -1.7rem;
      border: none;
      background-color: #dc5555;
      padding: 0.3rem 0.6rem;
      border-radius: 3.5px 0 0 3.55px;
      color: #fff;
      transition: all 0.15s ease-in-out;
      pointer-events: none;
      opacity: 0;
    }

    &:hover .delete-btn {
      pointer-events: auto;
      opacity: 1;
    }
  }
}

/* 響應式設計 */
@media (max-width: 768px) {
  .list li {
    padding: 0.75rem 0.625rem;

    .delete-btn {
      opacity: 1;
      pointer-events: auto;
      position: relative;
      left: auto;
      margin-left: 0.5rem;
      padding: 0.15rem 0.4rem;
      font-size: 0.85rem;
      border-radius: 3px;
    }
  }
}

@media (max-width: 480px) {
  .history-box {
    margin: 1.5rem 0;
  }

  .list {
    gap: 0.5rem;

    li {
      flex-wrap: wrap;

      span:first-child {
        width: 100%;
        margin-bottom: 0.25rem;
      }

      span:last-of-type {
        margin-right: auto;
      }
    }
  }
}
</style>
