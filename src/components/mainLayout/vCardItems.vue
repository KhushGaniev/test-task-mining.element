<template>
  <div class="card-items">
    <input
      type="text"
      class="input"
      placeholder="Search..."
      v-model="searchQuery"
    />

    <div class="container">
      <div class="card-items__wrapper">
        <vCard
          v-for="(item, index) in filteredPaintings"
          :key="index"
          :name="item.name"
          :image="item.image"
          :id="item.id"
        />
      </div>
    </div>
  </div>
</template>

<script>
import vCard from "@/components/mainLayout/vCard.vue";

export default {
  name: "vCardItems",
  components: {
    vCard,
  },
  data() {
    return {
      infoPokemon: [],
      searchQuery: "",
    };
  },
  methods: {
    async fetchCardsInformation() {
      try {
        const response = await fetch("https://pokeapi.co/api/v2/pokemon/");
        const data = await response.json();

        // Перебираем список покемонов и делаем дополнительные запросы для получения id и картинки каждого покемона
        const pokemonList = await Promise.all(
          data.results.map(async (pokemon) => {
            const pokemonResponse = await fetch(pokemon.url);
            const pokemonData = await pokemonResponse.json();

            return {
              name: pokemon.name,
              id: pokemonData.id,
              image: pokemonData.sprites.front_default,
            };
          })
        );

        this.infoPokemon = pokemonList;
        console.log(this.infoPokemon);
      } catch (error) {
        console.error("Ошибка при выполнении запроса:", error);
      }
    },
  },
  mounted() {
    this.fetchCardsInformation();
  },
  computed: {
    filteredPaintings() {
      if (!this.infoPokemon) {
        return [];
      }
      if (!this.searchQuery) {
        return this.infoPokemon;
      }
      const searchLower = this.searchQuery.toLowerCase();
      return this.infoPokemon.filter((infoPokemon) => {
        return infoPokemon.name.toLowerCase().includes(searchLower);
      });
    },
  },
};
</script>

<style lang="scss" scoped>
.input {
  border: 1px solid red;
  width: 620px;
  height: 30px;
}
.container {
  max-width: 620px;
  margin: 0 auto;
}
.card-items {
  margin-top: 50px;
  &__wrapper {
    display: grid;
    grid-template-columns: repeat(5, 1fr);
    gap: 15px;
  }
}
</style>
