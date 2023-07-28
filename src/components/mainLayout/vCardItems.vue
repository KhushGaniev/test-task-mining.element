<template>
  <div class="card-items">
    <div class="container">
      <div class="card-items__wrapper">
        <vCard
          v-for="(item, index) in infoPokemon"
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
};
</script>

<style lang="scss" scoped>
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
