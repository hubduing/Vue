<script setup>
const emit = defineEmits(['response'])

emit('response', 'привет от дочернего компонента')
</script>

<template>
  <h2>Дочерний компонент</h2>
</template>