<template>
  <main class="main">
    <div class="main__container">
      <div class="main__panel">
        <FilterPanel />
      </div>
      <ProductGrid />
    </div>
  </main>
</template>

<script>
import FilterPanel from "./FilterPanel.vue";
import ProductGrid from "./ProductGrid.vue";
export default {
  components: {
    ProductGrid,
    FilterPanel,
  },
  name: "MainContent",
};
</script>

<style lang="scss" scoped>
.main {
  margin-top: 24px;
  height: 100%;
  @media (max-width: 950px) {
    margin: 0;
  }
  &__container {
    display: flex;
    gap: 36px;
  }
  &__panel {
    @media (max-width: 950px) {
      display: none;
    }
  }
}
</style>
