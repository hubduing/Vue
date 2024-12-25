<script setup>
import { ref } from 'vue'
import ChildComp from './ChildComp.vue'

const greeting = ref('Привет от родителя')
</script>

<template>
  <ChildComp :msg="greeting" />
</template>