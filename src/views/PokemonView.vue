<template>
  <div class="home">
    <vPokemonDetail />
  </div>
</template>

<script>
import vPokemonDetail from "@/components/page/vPokemonDetail.vue";

export default {
  name: "HomeView",
  components: {
    vPokemonDetail,
  },
};
</script>
