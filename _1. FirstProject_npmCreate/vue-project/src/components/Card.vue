<template>
  <div class="card">
    <h2>{{ card.name }}</h2>
    <p>Date: {{ card.date }}</p>
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: {
    card: Object,
  },
};
</script>

<style scoped>
.card {
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 10px;
  margin: 10px;
  text-align: center;
}
</style>
