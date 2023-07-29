<template>
  <div class="main">
    <div class="container">
      <vHeader />
      <vCardItems />
    </div>
  </div>
</template>

<script>
import vHeader from "@/components/vHeader.vue";
import vCardItems from "@/components/mainLayout/vCardItems.vue";

export default {
  name: "MainLayout",
  components: {
    vHeader,
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
