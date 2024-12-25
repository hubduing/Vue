<script setup>
import { ref } from 'vue'
 const message = ref("Make me dynamic!")
</script>

<template>
  <h1>{{message}}</h1>
</template>