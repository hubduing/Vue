<template>
  <h3>История</h3>
  <ul id="list" class="list">
    <li
      v-for="t in transactions"
      :key="t.id"
      :class="t.amount < 0 ? 'minus' : 'plus'"
    >
      {{ t.text }}
      <span>{{ t.amount }}руб</span><button class="delete-btn">x</button>
    </li>
  </ul>
</template>

<script setup>
import { defineProps } from "vue";
const props = defineProps({
  transactions: {
    type: Array,
    required: true,
  },
});
</script>
