<script setup>
import { ref, onMounted } from 'vue'

const pElementRef = ref(null)

onMounted(() => {
  pElementRef.value.textContent = "123";
})
</script>

<template>
  <p ref="pElementRef">Привет</p>
</template>