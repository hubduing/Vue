<script setup>
const props = defineProps({
  msg: String
})
</script>

<template>
  <h2>{{ msg || 'пока входные параметры не переданы' }}</h2>
</template>