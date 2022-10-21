<script >
import axios from 'axios';

export default {
  name: "App",
  components: {},
  data() {
    return {
      pokemons: [],
    }
  },

  mounted() {
    axios.get('https://pokeapi.co/api/v2/pokemon?limit=100&offset=200').then((response) => {
      this.pokemons = response.data.results;
    })
  }
}
</script>

<template>
 <div class="container">
  <div class="card" v-for="pokemon in pokemons" :key="pokemon.name"><h1>{{pokemon.name}}</h1></div>
 </div>
</template>

<style>
.card {
  width: 25%;
  border-radius: 15px;
  border: 1px solid black;
  margin: 10px 5px;
}
.container {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}
</style>
