<template>
  <section class="filter">
    <FilterCategory />
    <FilterPrice />
    <FilterBrand />
    <FilterSize />
  </section>
</template>

<script>
import FilterCategory from "./FilterCategory.vue";
import FilterPrice from "./FilterPrice.vue";
import FilterBrand from "./FilterBrand.vue";
import FilterSize from "./FilterSize.vue";
export default {
  name: "FilterPanel",
  components: { FilterCategory, FilterPrice, FilterBrand, FilterSize },
};
</script>

<style scoped lang="scss">
.filter {
  display: flex;
  flex-direction: column;
  gap: 28px;
  min-width: 280px;
  @media (max-width: 600px) {
    gap: 10px;
    min-width: 250px;
  }
}
</style>
