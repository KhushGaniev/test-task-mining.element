<template>
  <header class="main">
    <div class="container">
      <MySearch :placeholder="'Введите имя покемона'" />
      <vCardItems />
    </div>
  </header>
</template>

<script>
import MySearch from "@/components/UI/MySearch.vue";
import vCardItems from "@/components/mainLayout/vCardItems.vue";

export default {
  name: "vHeader",
  components: {
    MySearch,
    vCardItems,
  },
};
</script>

<style lang="scss" scoped>
.main {
  padding: 0 10px;
}
.container {
  max-width: 620px;
  margin: 0 auto;
}
</style>
