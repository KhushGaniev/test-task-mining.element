<template>
  <div class="card">
    <div class="container">
      <div class="card__wrapper">
        <div>
          <img :src="image" alt="icon" />
        </div>
        <h2 class="card__name">{{ name }}</h2>
        <button class="card__btn" @click="$router.push(`/detail/${id}`)">
          Подробнее
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "vCard",
  props: {
    name: {
      type: String,
    },
    image: {
      type: String,
    },
    id: {
      type: Number,
    },
  },
  methods: {
    redirectToDetailPage() {
      this.$router.push({ name: "detail", params: { id: this.id } });
    },
  },
};
</script>

<style lang="scss" scoped>
.container {
  width: 112px;
  height: 179px;
}
.card {
  border-radius: 4px;
  background: #fff;
  box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.15);
  &__wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  &__name {
    margin-bottom: 22px;
    color: #1e1e1e;
    font-size: 16px;
    font-weight: 500;
  }
  &__btn {
    width: 96px;
    height: 24px;
    border-radius: 4px;
    background: #b5dbdd;
    color: #1e1e1e;
    font-size: 12px;
    font-weight: 400;
    text-transform: lowercase;
  }
}
</style>
