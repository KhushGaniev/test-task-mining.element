<template>
  <div class="card-items">
    <div class="container">
      <div class="card-items__wrapper">
        <vCard
          v-for="(item, index) in infoPokemon"
          :key="index"
          :name="item.name"
          :image="item.image"
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
        this.infoPokemon = data.results;

        // Запускаем асинхронный цикл для получения изображений
        for (const pokemon of this.infoPokemon) {
          try {
            const imageResponse = await fetch(pokemon.url);
            const imageData = await imageResponse.json();
            pokemon.image = imageData.sprites.front_default;
            console.log();
          } catch (error) {
            console.error("Ошибка при получении изображения:", error);
          }
        }

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
