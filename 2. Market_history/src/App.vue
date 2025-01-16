<template>
  <Header />
  <div class="container">
    <Balance :total="+total" />
    <InOutExpense :income="+income" :expenses="+expenses" />
    <Transaction
      :transactions="transactions"
      @transactionDeleted="handleTransactionDelete"
    />
    <AddTransaction @transactionSubmit="handleTransactionSubmit" />
  </div>
</template>

<script setup>
import AddTransaction from "./components/AddTransaction.vue";
import Balance from "./components/Balance.vue";
import Header from "./components/Header.vue";
import InOutExpense from "./components/InOutExpense.vue";
import Transaction from "./components/Transaction.vue";
import { useToast } from "vue-toastification";
import { ref, computed, onMounted } from "vue";

const toast = useToast();

const transactions = ref([
//   { id: 1, text: "Цветы", amount: -100 },
//   { id: 2, text: "Мяч", amount: -900 },
//   { id: 3, text: "Продажа виктории", amount: 450 },
//   { id: 4, text: "Тортик", amount: -650 },
]);

onMounted(() => {
  const savedTransactions = JSON.parse(localStorage.getItem("transactions"));

  if (savedTransactions) {
    transactions.value = savedTransactions;
  }
});

const total = computed(() => {
  return transactions.value.reduce((acc, transaction) => {
    return acc + transaction.amount;
  }, 0);
});

const calculateIncome = () => {
  return transactions.value
    .filter((transaction) => transaction.amount > 0)
    .reduce((acc, transaction) => {
      return acc + transaction.amount;
    }, 0);
};

const calculateExpenses = () => {
  return transactions.value
    .filter((transaction) => transaction.amount < 0)
    .reduce((acc, transaction) => {
      return acc + transaction.amount;
    }, 0);
};

const income = computed(() => calculateIncome().toFixed(2));
const expenses = computed(() => calculateExpenses().toFixed(2));

const handleTransactionSubmit = (transactionData) => {
  transactions.value.push({
    id: generateUniqueId(),
    text: transactionData.text,
    amount: transactionData.amount,
  });

  saveToLocalStorage();

  toast.success("Транзакция добавлена");
  //   console.log(generateUniqueId());
};

const generateUniqueId = () => {
  return Math.floor(Math.random() * 1000000);
};

const handleTransactionDelete = (id) => {
  transactions.value = transactions.value.filter(
    (transaction) => transaction.id !== id
  );

  saveToLocalStorage();

  toast.success("Транзакция была удалена");
};

const saveToLocalStorage = () => {
  localStorage.setItem("transactions", JSON.stringify(transactions.value));
};
</script>
