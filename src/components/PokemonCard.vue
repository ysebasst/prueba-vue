<template>
  <div class="pokemon-card">
    <h3 class="pokemon-nombre">{{ pokemon.name || "Pokemon" }}</h3>
    <div class="pokemon-imagen">
      <img :src="pokemon.sprites.front_default" alt="image" />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      pokemon: {
        sprites:{
          front_defaul: ""
        }
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
  width: 100%;
}
</style>
