<template>
  <div :class="theme">
    <Header />
    <button @click="toggleTheme" class="theme-toggle">Toggle Theme</button>
    <CardList />
    <Footer />
  </div>
</template>

<script>
import CardList from './components/CardList.vue';
import Header from './components/Header.vue';
import Footer from './components/Footer.vue';

export default {
  name: 'App',
  components: {
    CardList,
    Header,
    Footer,
  },
  data() {
    return {
      theme: 'dark-theme',
    };
  },
  methods: {
    toggleTheme() {
      this.theme = this.theme === 'dark-theme' ? 'light-theme' : 'dark-theme';
    },
  },
};
</script>

<style>
:root {
  --background-color: #121212;
  --text-color: #ffffff;
  --card-background: #1e1e1e;
  --button-background: #ff4d4d;
  --button-color: white;
}

.light-theme {
  --background-color: #ffffff;
  --text-color: #000000;
  --card-background: #f0f0f0;
  --button-background: #007bff;
  --button-color: white;
}

.dark-theme {
  --background-color: #121212;
  --text-color: #ffffff;
  --card-background: #1e1e1e;
  --button-background: #ff4d4d;
  --button-color: white;
}

body {
  background-color: var(--background-color);
  color: var(--text-color);
  margin: 0;
  font-family: Arial, sans-serif;
}

header {
  display: flex;
  justify-content: flex-end;
  padding: 10px;
}

.theme-toggle {
  margin: 10px;
  padding: 10px;
  background-color: var(--button-background);
  color: var(--button-color);
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
</style>
