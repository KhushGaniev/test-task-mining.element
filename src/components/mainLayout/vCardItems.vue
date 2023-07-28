<template>
  <div class="card-items">
    <div class="container">
      <div class="card-items__wrapper">
        <vCard />
        <vCard />
        <vCard />
        <vCard />
        <vCard />
        <vCard />
        <vCard />
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
