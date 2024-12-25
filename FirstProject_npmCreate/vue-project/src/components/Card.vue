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
  background-color: var(--card-background);
  color: var(--text-color);
  border: 1px solid #ccc;
  padding: 20px;
  margin: 10px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: flex-start;
  width: 300px; /* Увеличиваем ширину карточки */
  border-radius: 8px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
  transition: background-color 0.3s, color 0.3s;
}

.remove-button {
  background-color: var(--button-background);
  color: var(--button-color);
  border: none;
  padding: 10px 15px;
  cursor: pointer;
  border-radius: 5px;
  margin-top: 10px;
}

@media (max-width: 600px) {
  .card {
    width: 100%; /* Ширина карточки 100% на мобильных */
  }
}
</style>
