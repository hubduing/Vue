<script setup>
import { ref } from 'vue'
import ChildComp from './ChildComp.vue'

const msg = ref('от родителя')
</script>

<template>
  <ChildComp>Сообщение: {{ msg }}</ChildComp>
</template>