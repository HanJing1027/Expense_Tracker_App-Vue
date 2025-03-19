<template>
  <div class="add-transaction-box">
    <h3>Add new transaction</h3>
    <form>
      <div class="form-control">
        <label for="text">內容</label>
        <input id="text" type="text" placeholder="請輸入內容..." />
      </div>

      <div class="form-control">
        <label for="amount">金額</label>
        <input type="number" id="amount" placeholder="請輸入金額..." />
      </div>

      <div class="category-control">
        <label>
          <input type="radio" name="category" value="plus" />
          <span class="bubble plus"></span>
          <p>收入</p>
        </label>

        <label>
          <input type="radio" name="category" value="minus" />
          <span class="bubble minus"></span>
          <p>支出</p>
        </label>
      </div>

      <button @click.prevent class="btn">添加款項紀錄</button>
    </form>
  </div>
</template>

<script setup></script>

<style lang="scss" scoped>
@import '../assets/styles/variables';

.add-transaction-box {
  width: 100%;

  h3 {
    @include subtitle;
  }

  .form-control {
    display: flex;
    flex-direction: column;
    margin: 20px 0;
  }
}

.form-control {
  label {
    color: #666;
  }

  input {
    margin-top: 10px;
    width: 100%;
    height: 40px;
    border: none;
    border-radius: 5px;
    padding: 0 10px;
    outline: none;
    box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.1);

    /* Chrome, Safari, Edge */
    &[type='number']::-webkit-inner-spin-button,
    &[type='number']::-webkit-outer-spin-button {
      appearance: none;
      margin: 0;
    }

    /* Firefox */
    &[type='number'] {
      -moz-appearance: textfield;
    }
  }
}

.category-control {
  display: flex;
  justify-content: space-between;

  label {
    position: relative;
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 48%;
    padding: 1.25rem 0.5rem;
    border-radius: 8px;
    cursor: pointer;
    transition: all 0.3s ease;
    background-color: #f9f9f9;

    &:hover {
      background-color: #f5f5f5;
    }

    input[type='radio'] {
      position: absolute;
      opacity: 0;

      &:checked + .bubble::before {
        opacity: 1;
        transform: scale(1);
      }

      &:checked + .bubble {
        border-width: 2px;
      }

      &:checked ~ p {
        font-weight: 600;
      }

      &:checked + .bubble.plus {
        box-shadow: 0 0 0 2px rgba(76, 175, 80, 0.3);
      }

      &:checked + .bubble.minus {
        box-shadow: 0 0 0 2px rgba(220, 85, 85, 0.3);
      }

      &:checked ~ .bubble.plus + p {
        color: #4caf50;
      }

      &:checked ~ .bubble.minus + p {
        color: #dc5555;
      }
    }
  }

  .bubble {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 2rem;
    height: 2rem;
    border-radius: 50%;
    border: 1px solid #ddd;
    margin-bottom: 0.75rem;
    transition: all 0.3s ease;
    position: relative;

    &::before {
      content: '';
      position: absolute;
      width: 65%;
      height: 65%;
      border-radius: 50%;
      opacity: 0;
      transform: scale(0);
      transition:
        transform 0.3s ease,
        opacity 0.3s ease;
    }

    &.plus {
      &::before {
        background-color: #4caf50;
      }

      &:hover {
        border-color: #4caf50;
      }
    }

    &.minus {
      &::before {
        background-color: #dc5555;
      }

      &:hover {
        border-color: #dc5555;
      }
    }
  }

  p {
    font-size: 1rem;
    margin: 0;
    color: #666;
    transition: color 0.3s ease;
  }
}

// 響應式設計
@media (max-width: 480px) {
  .category-control {
    flex-direction: column;
    gap: 0.75rem;

    label {
      width: 100%;
      flex-direction: row;
      justify-content: flex-start;
      padding: 0.75rem 1rem;

      .bubble {
        margin-bottom: 0;
        margin-right: 1rem;
      }
    }
  }
}

.btn {
  display: block;
  width: 100%;
  padding: 0.75rem;
  background-color: #9c89fe;
  color: #fff;
  border: none;
  border-radius: 5px;
  font-size: 1rem;
  cursor: pointer;
  transition: all 0.3s ease;

  &:hover {
    background-color: darken(#9c89fe, 10%);
    box-shadow: 0px 4px 8px #00000033;
  }
}
</style>
