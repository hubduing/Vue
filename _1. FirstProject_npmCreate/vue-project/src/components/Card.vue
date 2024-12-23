<template>
  <div class="card">
    <h3>{{ card.name }}</h3>
    <p>{{ card.date }}</p>
    <button @click="$emit('remove')" class="remove-button">Remove</button>
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
  padding: 10px;
  margin: 10px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.remove-button {
  background-color: #ff4d4d;
  color: white;
  border: none;
  padding: 5px 10px;
  cursor: pointer;
}
</style>
