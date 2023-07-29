<template>
  <header class="header">
    <div class="container">
      <MySearch :placeholder="'Введите имя покемона'" />
    </div>
  </header>
</template>

<script>
import MySearch from "@/components/UI/MySearch.vue";

export default {
  name: "vHeader",
  components: {
    MySearch,
  },
};
</script>

<style lang="scss" scoped>
.header {
  margin-bottom: 50px;
}
.container {
  max-width: 620px;
  margin: 0 auto;
}
</style>
