<template>
  <div id="app">
    <h1>Gatitos</h1>
    
    <catCard
      v-for="cat in cats"
      :key="cat.id"
      :id="cat.id"
      :name="cat.name"
      :color="cat.color"
      :code-name="cat.codeNale"
      :is-favorite="cat.isFavorite"
      @toggle-favorite="toggleFavoriteStatus"
    />
  </div>
</template>

<script>
import catCard from './components/catCard';

export default {
  name: 'App',
  data() {
    return {
      cats: [
        {
          id: 'niro',
          name: 'Niro',
          color: 'Negro y blanco',
          codeName: 'Gato flaco',
          isFavorite: true
        },
        {
          id: 'rupert',
          name: 'Rupert',
          color: 'Gris y blanco',
          codeName: 'Pupi',
          isFavorite: true
        }
      ]
    }
  },
  components: {
    catCard
  },
  methods: {
    toggleFavoriteStatus(catId) {
      console.log('hello there');
      const thisCat = this.cats.find(cat => cat.id === catId);
      console.log(thisCat.isFavorite);
      thisCat.isFavorite = !thisCat.isFavorite;
      console.log(thisCat.isFavorite);
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
