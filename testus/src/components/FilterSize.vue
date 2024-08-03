<template>
  <div class="size">
    <div class="size__title">Размер</div>
    <ul class="size__list">
      <li v-for="(size, index) in filteredSizes" :key="index">
        <input
          type="checkbox"
          :id="'size_' + index"
          v-model="selectedSizes"
          :value="size.name"
        />
        <label :for="'size_' + index"
          >{{ size.name }}
          <span>
            {{ size.amount }}
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
      sizes: [
        { name: "Размер 1", amount: 3 },
        { name: "Размер 2", amount: 3 },
        { name: "Размер 3", amount: 3 },
        { name: "Размер 4", amount: 3 },
        { name: "Размер 5", amount: 5 },
        { name: "Размер 6", amount: 3 },
      ],
      selectedSizes: [],
    };
  },
  computed: {
    filteredSizes() {
      return this.sizes;
    },
  },
};
</script>

<style scoped lang="scss">
.size {
  display: flex;
  flex-direction: column;
  gap: 16px;
  &__title {
    font-weight: bold;
    color: rgb(51, 51, 51);
    font-family: PT Sans;
    font-size: 16px;
    font-weight: 700;
    line-height: 20px;
    text-align: center;
  }
  &__list {
    list-style-type: none;
    padding: 0;
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
