<template>
  <div class="pokemon-card">
    <h3 class="pokemon-nombre">{{ pokemon.name || "Pokemon" }}</h3>
    <div class="pokemon-imagen">
      <img :src="pokemon.sprites.front_default" alt="image" />
    </div>
    <div class="pokemon-stats-title">Stats</div>
    <div v-for="p of pokemon.stats" :key="p.stat.url" class="pokemon-stats">
      <span>{{ p.stat.name }}</span>
      <span>{{ p.base_stat }}</span>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      pokemon: {
        stats: [],
        sprites: {
          front_defaul: "",
        },
      },
    };
  },
  props: {
    url: String,
  },
  created() {
    this.obtenerPokemon();
  },
  methods: {
    obtenerPokemon() {
      fetch(this.url)
        .then((res) => res.json())
        .catch((err) => console.log(err))
        .then((data) => {
          this.pokemon = data;
          console.log(data);
        });
    },
  },
};
</script>

<style scoped>
.pokemon-card {
  background-color: #ddd;
  padding: 1em;
  border-radius: 5px;
}
.pokemon-nombre {
  font-size: 1.5em;
  font-weight: bold;
  text-align: center;
}
.pokemon-imagen {
  display: flex;
  justify-content: center;
  align-items: center;
}
.pokemon-stats-title {
  text-align: center;
  font-weight: bold;
  background-color: #bbb;
}
.pokemon-stats {
  display: flex;
  justify-content: space-between;
  padding: 0.1em 0.5em;
  border: 1px solid #bbb;
}
</style>
