<template>
  <button class="btn">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: "MyButton",
};
</script>

<style lang="scss" scoped>
.btn {
  width: 96px;
  height: 24px;
  border-radius: 4px;
  background: #b5dbdd;
  color: #1e1e1e;
  font-size: 12px;
  font-weight: 400;
  text-transform: lowercase;
}
</style>
