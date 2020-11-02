<template>
  <section class="container">
    <div class="pokemons-container">
      <PokemonCard v-for="p of pokemons" :key="p.url" :url="p.url"/>
    </div>
  </section>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";
import PokemonCard from "@/components/PokemonCard.vue";

const API = "https://pokeapi.co/api/v2";

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
.container{
  max-width: 1024px;
  margin: auto;
}
.pokemons-container {
  padding: 1em;
  display: grid;
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
