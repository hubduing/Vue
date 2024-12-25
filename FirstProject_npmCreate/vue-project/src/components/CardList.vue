<template>
  <div>
    <div class="controls">
      <input v-model="search" placeholder="Search by name" />
      <input type="date" v-model="dateSearch" placeholder="Search by date" />
      <button @click="sortByDate">Sort by Date</button>
    </div>
    <div class="new-card-controls">
      <input v-model="newCardName" placeholder="Card Name" />
      <input type="date" v-model="newCardDate" placeholder="Card Date" />
      <button @click="addCard">Add Card</button>
    </div>
    <div class="card-list">
      <Card 
        v-for="card in filteredCards" 
        :key="card.id" 
        :card="card" 
        @remove="removeCard(card.id)" 
      />
    </div>
  </div>
</template>

<script>
import Card from './Card.vue';

export default {
  name: 'CardList',
  components: {
    Card,
  },
  data() {
    return {
      search: '',
      dateSearch: '',
      newCardName: '',
      newCardDate: '',
      nextId: 4,
      cards: [
        { id: 1, name: 'Card 1', date: '2024-01-01' },
        { id: 2, name: 'Card 3', date: '2026-03-01' },
        { id: 3, name: 'Card 2', date: '2025-02-01' },
      ],
    };
  },
  computed: {
    filteredCards() {
      return this.cards.filter(card => {
        const matchesName = card.name.toLowerCase().includes(this.search.toLowerCase());
        const matchesDate = this.dateSearch ? card.date === this.dateSearch : true;
        return matchesName && matchesDate;
      });
    },
  },
  methods: {
    sortByDate() {
      this.cards.sort((a, b) => new Date(a.date) - new Date(b.date));
    },
    addCard() {
      if (this.newCardName && this.newCardDate) {
        this.cards.push({
          id: this.nextId++,
          name: this.newCardName,
          date: this.newCardDate,
        });
        this.newCardName = '';
        this.newCardDate = '';
      } else {
        alert('Please fill in both fields.');
      }
    },
    removeCard(id) {
      this.cards = this.cards.filter(card => card.id !== id);
    },
  },
};
</script>

<style scoped>
.card-list {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}

.controls, .new-card-controls {
  display: flex;
  justify-content: space-between;
  margin-bottom: 20px;
}

input {
  padding: 10px;
  margin-right: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  flex: 1;
}

button {
  padding: 10px 15px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.new-card-controls {
  margin-top: 20px;
}

@media (max-width: 600px) {
  .card {
    width: 100%; /* Ширина карточки 100% на мобильных */
  }

  .controls, .new-card-controls {
    flex-direction: column; /* Вертикальное размещение на мобильных */
  }

  input {
    margin: 5px 0; /* Уменьшаем отступы между полями */
  }
}
</style>
