<template>
  <div class="card">
    <div class="container">
      <div class="card__wrapper">
        <div>
          <img src="@/assets/images/iconBulbasaur.svg" alt="icon" />
        </div>
        <h2 class="card__name">iconBulbasaur</h2>
        <button class="card__btn">Подробнее</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "vCard",
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
