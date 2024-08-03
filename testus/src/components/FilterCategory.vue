<template>
  <div class="category">
    <div class="category__title">
      Название категории <span>{{ categories.length }}</span>
    </div>
    <ul class="category__list">
      <li
        v-for="category in categories"
        :key="category.value"
        class="category__item"
        :class="{
          'category__item--active': isSelected(category),
        }"
        @click="toggleCategory(category)"
      >
        {{ category.name }} <span>{{ category.value }}</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      categories: [
        { value: 1, name: "Категория 3" },
        { value: 2, name: "Категория 2" },
        { value: 3, name: "Категория 3" },
      ],
      selectedCategories: [],
    };
  },
  methods: {
    isSelected(category) {
      return this.selectedCategories.some((c) => c.value === category.value);
    },
    toggleCategory(category) {
      if (this.isSelected(category)) {
        this.selectedCategories = this.selectedCategories.filter(
          (c) => c.value !== category.value
        );
      } else {
        this.selectedCategories.push(category);
      }
    },
  },
};
</script>

<style scoped lang="scss">
.category {
  &__title,
  &__item {
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: nowrap;
    white-space: nowrap;
    padding: 7px 8px;
    color: rgb(51, 51, 51);
    font-family: PT Sans;
    font-size: 14px;
    font-weight: 400;
    line-height: 16px;
    border-radius: 5px;
    cursor: pointer;
    span {
      color: rgb(170, 170, 170);
      font-size: 12px;
      font-weight: 400;
      line-height: 14px;
    }
  }
  &__item {
    transition: all 0.1s ease-in;
    &:hover {
      background-color: #e2efff;
    }
    &--active {
      background-color: var(--color-brand);
      color: white;
      span {
        color: white;
      }
      &:hover {
        background-color: #3b5fba;
      }
    }
  }
  &__list {
    margin-left: 32px;
  }
}
</style>
