<template>
  <div
    class="product"
    :class="{ 'product--unavailable': !product.isAvailable }"
  >
    <div class="product__preview">
      <img src="../assets/icons/empty-product.svg" alt="empty" />
      <div v-if="product.onFire" class="product__fire">
        Хит продаж
        <img src="../assets/icons/fire.svg" alt="fire" />
      </div>
      <div v-if="discount" class="product__discount">-{{ discount }}%</div>
    </div>
    <div class="product__details">
      <div class="product__brand">{{ product.brand }}</div>
      <div class="product__name">{{ product.name }}</div>
      <div v-if="product.isAvailable" class="product__price">
        {{ product.price }} ₽
        <span v-if="product.oldPrice">{{ product.oldPrice }} ₽</span>
      </div>
      <button
        v-if="product.isAvailable"
        class="product__buy"
        :disabled="!product.isAvailable"
      >
        Купить
      </button>

      <div
        v-if="!product.isAvailable"
        class="product__unavailable"
        :disabled="!product.isAvailable"
      >
        Сообщить о поступлении
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProductCard",
  props: {
    product: {
      type: Object,
      required: true,
      validator(value) {
        return (
          "onFire" in value &&
          "brand" in value &&
          "name" in value &&
          "price" in value &&
          "oldPrice" in value &&
          "isAvailable" in value
        );
      },
    },
  },
  computed: {
    discount() {
      if (this.product.oldPrice && this.product.price) {
        const discountPercentage =
          ((this.product.oldPrice - this.product.price) /
            this.product.oldPrice) *
          100;
        return Math.round(discountPercentage);
      }
      return null;
    },
  },
};
</script>

<style scoped lang="scss">
@keyframes scale-fire {
  0% {
    transform: rotate(0deg);
  }
  20% {
    transform: rotate(-25deg);
  }
  40% {
    transform: rotate(25deg);
  }
  60% {
    transform: rotate(-25deg);
  }
  80% {
    transform: rotate(25deg);
  }
  100% {
    transform: rotate(0deg);
  }
}
.product {
  max-width: 333px;
  width: 100%;
  cursor: pointer;
  transition: all 0.2s ease-in;

  &:hover:not(.product--unavailable) {
    transform: scale(1.07);
    .product__fire img {
      animation: scale-fire 1s 1 alternate;
    }
    .product__buy {
      background-color: rgb(115, 151, 245);
      color: white;
      &:active {
        background-color: rgb(76, 115, 214);
      }
    }
  }

  &__preview {
    width: 100%;
    height: 200px;
    background-color: #f8f8fa;
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  &__fire {
    position: absolute;
    top: 12px;
    left: 12px;
    padding: 8px 10px;
    border: 1px solid rgb(242, 242, 242);
    border-radius: 4px;
    background: rgb(255, 255, 255);
    display: flex;
    align-content: center;
    box-sizing: border-box;
    font-family: PT Sans;
    font-size: 14px;
    font-weight: 400;
    line-height: 16px;
    img {
      margin-left: 8px;
    }
  }
  &__discount {
    position: absolute;
    bottom: 12px;
    left: 12px;
    color: var(--color-white);
    font-family: PT Sans;
    font-size: 14px;
    font-weight: 700;
    line-height: 14px;
    border-radius: 4px;
    background: rgb(115, 151, 245);
    padding: 6px 10px;
  }
  &__brand {
    margin-top: 16px;
    color: rgb(170, 170, 170);
    font-family: PT Sans;
    font-size: 14px;
    font-weight: 400;
    line-height: 16px;
  }

  &__name {
    margin-top: 8px;
    color: rgb(51, 51, 51);
    font-family: PT Sans;
    font-size: 14px;
    font-weight: 400;
    line-height: 16px;
    overflow: hidden;
    text-overflow: ellipsis;
    display: -webkit-box;
    -webkit-line-clamp: 3;
    -webkit-box-orient: vertical;
    max-width: 168px;

    height: calc(16px * 3);
    transition: all 0.2s ease-in;
  }
  &:hover:not(.product--unavailable) {
    .product__name {
      color: rgb(18, 91, 174);
    }
  }
  &__price {
    color: rgb(51, 51, 51);
    font-family: PT Sans;
    font-size: 16px;
    font-weight: 700;
    line-height: 14px;
    display: flex;
    align-content: center;
    span {
      color: rgb(170, 170, 170);
      font-family: PT Sans;
      font-size: 12px;
      font-weight: 400;
      line-height: 14px;
      text-decoration-line: line-through;
      margin-left: 8px;
    }
  }
  &__buy {
    margin-top: 16px;
    padding: 12px 16px 12px 16px;
    box-sizing: border-box;
    border: 1px solid rgb(115, 151, 245);
    border-radius: 4px;
    background: rgb(255, 255, 255);
    color: rgb(115, 151, 245);
    font-family: PT Sans;
    font-size: 14px;
    font-weight: 700;
    line-height: 14px;
    transition: all 0.1s ease-in;
    cursor: pointer;
  }
  &__unavailable {
    width: 100%;
    margin-top: 30px;
    padding: 12px 0;
    display: flex;
    align-content: center;
    justify-content: center;
    border: 1px solid rgb(170, 170, 170);
    border-radius: 4px;
    background: rgb(255, 255, 255);
    color: rgb(170, 170, 170);
    font-family: PT Sans;
    font-size: 14px;
    font-weight: 700;
    line-height: 14px;
    cursor: pointer;
    transition: all 0.2s ease-in;
    &:hover {
      background: rgb(170, 170, 170);
      color: rgb(255, 255, 255);
    }
  }
  &--unavailable {
    cursor: not-allowed;
  }
}
</style>
