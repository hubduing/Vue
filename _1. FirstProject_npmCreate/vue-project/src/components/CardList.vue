<template>
  <div>
    <div>
      <input v-model="search" placeholder="Search by name" />
      <input type="date" v-model="dateSearch" placeholder="Search by date" />
      <button @click="sortByDate">Sort by Date</button>
    </div>
    <div class="card-list">
      <Card v-for="card in filteredCards" :key="card.id" :card="card" />
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
  },
};
</script>

<style scoped>
.card-list {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}
</style>
