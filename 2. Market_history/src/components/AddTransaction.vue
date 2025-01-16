<template>
  <h3>Добавить транзакцию</h3>
  <form id="form" @submit.prevent="onSubmit">
    <!-- Исправлено from на form -->
    <div class="form-control">
      <label for="text">Текст</label>
      <input
        type="text"
        id="text"
        v-model="text"
        placeholder="Введите текст..."
      />
    </div>

    <div class="form-control">
      <label for="amount"
        >Сумма <br />
        (отрицательное - расход, положительное - доход)
      </label>
      <input
        type="text"
        id="amount"
        v-model="amount"
        placeholder="Введите сумму"
      />
    </div>
    <button class="btn">Добавить транзакцию</button>
    <!-- Исправлено транщакцию на транзакцию -->
  </form>
</template>

<script setup>
import { ref } from "vue";
import { useToast } from "vue-toastification";

const text = ref("");
const amount = ref("");
const toast = useToast();
const emit = defineEmits(["transactionSubmit"]);

const onSubmit = () => {
  if (!text.value || !amount.value) {
    toast.error("Оба поля должны быть заполнены");
    return;
  }

  const transactionData = {
    // Переместили создание объекта сюда
    text: text.value,
    amount: parseFloat(amount.value),
  };

  emit("transactionSubmit", transactionData); // Теперь transactionData доступен

  text.value = "";
  amount.value = "";
};
</script>
