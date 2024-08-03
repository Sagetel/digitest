<template>
  <div class="brand">
    <div class="brand__title">
      Бренд
      <span @click="clearSelection">Очистить</span>
    </div>
    <div class="brand__input">
      <img class="brand__lupa" src="../assets/icons/lupa.svg" alt="lupa" />
      <input type="text" placeholder="Поиск" v-model="searchText" />
      <div
        v-if="searchText.length > 0"
        class="brand__cross"
        @click.stop="clearSearch"
      >
        <img src="../assets/icons/cross.svg" alt="X" />
      </div>
    </div>
    <ul class="brand__list">
      <li v-for="(brand, index) in filteredBrands" :key="index">
        <input
          type="checkbox"
          :id="'brand_' + index"
          v-model="selectedBrands"
          :value="brand.name"
        />
        <label :for="'brand_' + index">
          {{ brand.name }}
          <span>
            {{ brand.amount }}
          </span>
        </label>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      brands: [
        { name: "Атрибут 1", amount: 10 },
        { name: "Атрибут 2", amount: 5 },
        { name: "Атрибут 3", amount: 8 },
        { name: "Атрибут 4", amount: 12 },
        { name: "Атрибут 5", amount: 5 },
        { name: "Атрибут 6", amount: 12 },
        { name: "Атрибут 7", amount: 12 },
        { name: "Атрибут 8", amount: 12 },
        { name: "Атрибут 9", amount: 12 },
        { name: "Атрибут 10", amount: 12 },
        { name: "Атрибут 11", amount: 12 },
      ],
      selectedBrands: [],
      searchText: "",
    };
  },
  computed: {
    filteredBrands() {
      const searchText = this.searchText.toLowerCase();
      return this.brands.filter((brand) =>
        brand.name.toLowerCase().includes(searchText)
      );
    },
  },
  methods: {
    clearSelection() {
      this.selectedBrands = [];
    },
    // Метод для очистки текста поиска
    clearSearch() {
      this.searchText = "";
    },
  },
};
</script>

<style scoped lang="scss">
.brand {
  display: flex;
  flex-direction: column;
  gap: 16px;
  &__title {
    color: rgb(51, 51, 51);
    font-family: PT Sans;
    font-size: 16px;
    font-weight: 700;
    line-height: 20px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    span {
      color: rgb(170, 170, 170);
      font-family: PT Sans;
      font-size: 12px;
      font-weight: 400;
      line-height: 12px;
      cursor: pointer;
    }
  }
  &__input {
    display: flex;
    align-items: center;
    border: 1px solid rgb(213, 213, 213);
    border-radius: 4px;
    padding: 10px 12px 10px 12px;
    background: rgb(255, 255, 255);
    color: rgb(170, 170, 170);
    font-family: PT Sans;
    font-size: 14px;
    font-weight: 400;
    line-height: 16px;
    position: relative;
  }
  &__lupa {
    margin-right: 10px;
    opacity: 0.7;
  }
  &__cross {
    background-color: var(--color-font-main);
    opacity: 0.5;
    width: 16.67px;
    height: 16.67px;
    border-radius: 50%;
    flex-wrap: wrap;
    display: flex;
    align-content: center;
    justify-content: center;
    cursor: pointer;
    position: absolute;
    right: 12px;
    top: 50%;
    transform: translateY(-50%);
    transition: all 0.2s ease-in-out;

    &:hover {
      opacity: 1;
    }
  }
  &__list {
    list-style-type: none;
    padding: 0;
    max-height: 180px;
    overflow-y: scroll;
  }
  &__list li {
    margin-bottom: 5px;
    color: rgb(51, 51, 51);
    font-family: PT Sans;
    font-size: 14px;
    font-weight: 400;
    display: flex;
    align-items: center;
    transition: all 0.2s ease-in-out;
    &:hover {
      border-radius: 5px;
      background: rgb(226, 239, 255);
    }
  }
  &__list input[type="checkbox"] {
    margin-right: 5px;
  }
  label {
    color: rgb(51, 51, 51);
    font-family: PT Sans;
    font-size: 14px;
    font-weight: 400;
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 100%;
    span {
      margin-left: auto;
      padding-right: 16px;
      color: rgb(170, 170, 170);
      font-family: PT Sans;
      font-size: 12px;
      font-weight: 400;
    }
  }
}
</style>
