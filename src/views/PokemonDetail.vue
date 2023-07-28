<template>
  <div class="pokemon-detail">
    <div class="container">
      <div class="pokemon-detail__wrapper">
        <div>
          <img :src="image" alt="icon" />
        </div>
        <h2 class="pokemon-detail__name">{{ name }}</h2>
        <h3>Abilities:</h3>
        <ul>
          <li v-for="(item, index) in abilities" :key="index">
            {{ item }}
          </li>
        </ul>
        <h3>Stats:</h3>
        <ul>
          <li v-for="stat in stats" :key="stat.name">
            {{ stat.stat.name }}: {{ stat.base_stat }}
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "PokemonDetail",
  data() {
    return {
      name: "",
      image: "",
      abilities: [],
      stats: [],
    };
  },
  methods: {
    async fetchPokemonData(id) {
      try {
        const response = await fetch(
          `https://pokeapi.co/api/v2/pokemon/${id}/`
        );
        const data = await response.json();

        this.name = data.name;
        this.image = data.sprites.front_default;
        this.abilities = data.abilities.map((ability) => ability.ability.name);
        this.stats = data.stats;
      } catch (error) {
        console.error("Ошибка при выполнении запроса:", error);
      }
    },
  },
  async mounted() {
    const pokemonId = this.$route.params.id;
    await this.fetchPokemonData(pokemonId);
  },
};
</script>

<style>
/* Add your custom styles for the detailed Pokémon page here */
</style>
