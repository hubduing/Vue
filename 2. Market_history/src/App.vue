<template>
  <Header />
  <div class="container">
    <Balance />
    <InOutExpense />
    <Transaction />
    <AddTransaction />
  </div>
</template>

<script>
import AddTransaction from "./components/AddTransaction.vue";
import Balance from "./components/Balance.vue";
import Header from "./components/Header.vue";
import InOutExpense from "./components/InOutExpense.vue";
import Transaction from "./components/Transaction.vue";

export default {
  components: {
    Header,
    Balance,
    InOutExpense,
    Transaction,
    AddTransaction,
  },
};
</script>
