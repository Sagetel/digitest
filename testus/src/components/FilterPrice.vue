<template>
  <div class="price">
    <div class="price__title">Цена</div>
    <div class="price__sliders">
      <div class="price__slider-from">
        <span> от: </span>
        <input type="number" v-model="minPrice" @input="filterProducts" />
      </div>
      <img src="../assets/icons/palochka.svg" alt="-" />
      <div class="price__slider-to">
        <span> до: </span>
        <input type="number" v-model="maxPrice" @input="filterProducts" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      minPrice: null,
      maxPrice: null,
    };
  },
  methods: {
    filterProducts() {
      this.$emit("filter", {
        minPrice: this.minPrice,
        maxPrice: this.maxPrice,
      });
    },
  },
};
</script>

<style scoped lang="scss">
.price {
  &__title {
    font-weight: bold;
    color: rgb(51, 51, 51);
    font-family: PT Sans;
    font-size: 16px;
    font-weight: 700;
    line-height: 20px;
    text-align: center;
  }
  &__sliders {
    display: flex;
    justify-content: space-between;
    margin-top: 10px;
  }
  &__slider-from,
  &__slider-to {
    flex: 1;
    box-sizing: border-box;
    border: 1px solid rgb(213, 213, 213);
    border-radius: 4px;
    background: rgb(255, 255, 255);
    padding: 10px 8px 10px 8px;
    display: flex;
    align-items: center;
    max-width: 120px;
    span {
      color: rgb(170, 170, 170);
      font-family: PT Sans;
      font-size: 12px;
      font-weight: 400;
      line-height: 14px;
    }
  }
  &__slider-from input,
  &__slider-to input {
    width: 100%;
    padding: 0 5px;
    color: rgb(51, 51, 51);
    font-family: PT Sans;
    font-size: 14px;
    font-weight: 400;
  }
}
</style>
