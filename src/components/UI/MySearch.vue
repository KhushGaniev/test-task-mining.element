<template>
  <div class="search">
    <div class="container">
      <input class="search__input" :placeholder="placeholder" />
    </div>
  </div>
</template>

<script>
export default {
  name: "MySearch",
  props: {
    placeholder: {
      type: String,
    },
  },
};
</script>

<style lang="scss" scoped>
.container {
  margin: 0 auto;
  max-width: 620px;
}
.search {
  &__input {
    width: 620px;
    height: 40px;
    border-radius: 4px;
    background: #fff;
    box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.15);
    padding-left: 25px;
    &::placeholder {
      color: #1e1e1e;
      font-size: 12px;
      font-weight: 400;
    }
  }
}
</style>
