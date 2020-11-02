<template>
  <!-- <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div> -->
  <section class="pokemons-container">
    <!-- <img src="../assets/logo.png" alt="logo" /> -->
    <!-- <div v-for="p of pokemons" :key="p.url" class="pokemon-card">
      {{ p.name }}
    </div> -->
    <PokemonCard v-for="p of pokemons" :key="p.url" :url="p.url"/>
  </section>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";
import PokemonCard from "@/components/PokemonCard.vue";

const API = "http://pokeapi.co/api/v2";

export default {
  name: "Home",
  data() {
    return {
      pokemons: [],
    };
  },
  created() {
    this.obtenerPokemons();
  },
  methods: {
    obtenerPokemons() {
      fetch(`${API}/pokemon?limit=30&offset=0`)
        .then((res) => res.json())
        .catch((err) => console.log(err))
        .then((data) => {
          this.pokemons = data.results;
        });
    },
  },
  components: {
    HelloWorld,
    PokemonCard
  },
};
</script>

<style scoped>
.content {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}
.pokemons-container {
  padding: 1em;
  display: grid;
  grid-template-columns: repeat(1, 1fr);
  gap: 1em;
}
@media (min-width: 576px) {
  .pokemons-container {
    grid-template-columns: repeat(2, 1fr);
  }
}@media (min-width: 786px) {
  .pokemons-container {
    grid-template-columns: repeat(3, 1fr);
  }
}@media (min-width: 992px) {
  .pokemons-container {
    grid-template-columns: repeat(4, 1fr);
  }
}
</style>
