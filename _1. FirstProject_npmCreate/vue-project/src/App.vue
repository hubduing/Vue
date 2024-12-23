<script>
import Header from './components/Header.vue';
import CardList from './components/CardList.vue';
import Footer from './components/Footer.vue';

export default {
  name: 'App',
  components: {
    Header,
    CardList,
    Footer,
  },
};
</script>

<template>
  <div id="app">
    <Header />
    <main>
      <CardList />
    </main>
    <Footer />
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
main {
  padding: 20px;
}
</style>
