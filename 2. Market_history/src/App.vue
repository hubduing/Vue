<template>
  <Header />
  <div class="container">
    <Balance :total="total" />
    <InOutExpense :income="income" :expenses="expenses" />
    <Transaction :transactions="transactions" />
    <AddTransaction />
  </div>
</template>

<script setup>
import AddTransaction from "./components/AddTransaction.vue";
import Balance from "./components/Balance.vue";
import Header from "./components/Header.vue";
import InOutExpense from "./components/InOutExpense.vue";
import Transaction from "./components/Transaction.vue";
import { ref, computed } from "vue";

const transactions = ref([
  { id: 1, text: "Цветы", amount: -100 },
  { id: 2, text: "Мяч", amount: -900 },
  { id: 3, text: "Продажа виктории", amount: 450 },
  { id: 4, text: "Тортик", amount: -650 },
]);

const total = computed(() => {
  return transactions.value.reduce((acc, transaction) => {
    return acc + transaction.amount;
  }, 0);
});

const income = computed(() => {
  return transactions.value
    .filter((transaction) => transaction.amount > 0)
    .reduce((acc, transaction) => {
      return acc + transaction.amount;
    }, 0)
    .toFixed(2);
});

const expenses = computed(() => {
  return transactions.value
    .filter((transaction) => transaction.amount < 0)
    .reduce((acc, transaction) => {
      return acc + transaction.amount;
    }, 0)
    .toFixed(2);
});
</script>
