<template>
  <div class="inc-exp-box">
    <div>
      <h4>收入</h4>
      <p class="money plus">+$0,00</p>
    </div>
    <div>
      <h4>支出</h4>
      <p class="money minus">-$0,00</p>
    </div>
  </div>
</template>

<script setup></script>

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
