<template>
  <div class="history-box">
    <h3>History</h3>
    <ul class="list">
      <li class="plus">
        <span>與公司同事聚餐</span>
        <span>$-200</span>
        <button class="delete-btn">x</button>
      </li>

      <li class="minus">
        <span>月薪支入帳</span>
        <span>$+500</span>
        <button class="delete-btn">x</button>
      </li>
    </ul>
  </div>
</template>

<script setup></script>

<style lang="scss" scoped>
@import '../assets/styles/variables';

.history-box {
  margin: 2rem 0;
  width: 100%;

  h3 {
    @include subtitle;
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
      left: -1.4rem;
      border: none;
      background-color: #dc5555;
      padding: 0.2rem 0.5rem;
      border-radius: 3px;
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
