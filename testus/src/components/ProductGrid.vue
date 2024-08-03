<template>
  <section class="products">
    <div class="products__title">Название категории</div>
    <div class="products__wrapper">
      <ProductCard
        v-for="(product, index) in products"
        :key="index"
        :product="product"
      />
    </div>
  </section>
</template>

<script>
import ProductCard from "./ProductCard.vue";
export default {
  name: "ProductGrid",
  components: {
    ProductCard,
  },
  data() {
    return {
      products: [
        {
          onFire: true,
          brand: "Бренд",
          name: "Полное название товара в несколько строк для вида с обрывом в конце блаблаблабла цузщкзцушкзцщкузблаблаблабла цузщкзцу шкзцщк узблаблаблабла цузщкзцушкзцщкуз",
          price: 5990,
          oldPrice: 7990,
          isAvailable: true,
        },
        {
          onFire: true,
          brand: "Бренд",
          name: "Полное название товара в несколько строк для вида с обрывом в конце блаблаблабла цузщкзцушкзцщкуз",
          price: 5990,
          oldPrice: 8990,
          isAvailable: true,
        },
        {
          onFire: false,
          brand: "Бренд",
          name: "Полное название товара в несколько строк для вида с обрывом в конце блаблаблабла цузщкзцушкзцщкуз",
          price: 7000,
          oldPrice: 9090,
          isAvailable: true,
        },
        {
          onFire: true,
          brand: "Бренд",
          name: "Полное название товара в несколько строк для вида с обрывом в конце блаблаблабла цузщкзцушкзцщкуз",
          price: 5990,
          oldPrice: 0,
          isAvailable: true,
        },
        {
          onFire: false,
          brand: "Бренд",
          name: "Полное название товара в несколько строк для вида с обрывом в конце блаблаблабла цузщкзцушкзцщкуз",
          price: 4990,
          oldPrice: 0,
          isAvailable: false,
        },
        {
          onFire: true,
          brand: "Бренд",
          name: "Полное название товара в несколько строк для вида с обрывом в конце блаблаблабла цузщкзцушкзцщкуз",
          price: 5990,
          oldPrice: 7990,
          isAvailable: true,
        },
        {
          onFire: true,
          brand: "Бренд",
          name: "Полное название товара в несколько строк для вида с обрывом в конце блаблаблабла цузщкзцушкзцщкуз",
          price: 5990,
          oldPrice: 7990,
          isAvailable: true,
        },
        {
          onFire: true,
          brand: "Бренд",
          name: "Полное название товара в несколько строк для вида с обрывом в конце блаблаблабла цузщкзцушкзцщкуз",
          price: 5990,
          oldPrice: 7990,
          isAvailable: true,
        },
        {
          onFire: true,
          brand: "Бренд",
          name: "Полное название товара в несколько строк для вида с обрывом в конце блаблаблабла цузщкзцушкзцщкуз",
          price: 5990,
          oldPrice: 7990,
          isAvailable: true,
        },
        {
          onFire: true,
          brand: "Бренд",
          name: "Полное название товара в несколько строк для вида с обрывом в конце блаблаблабла цузщкзцушкзцщкуз",
          price: 5990,
          oldPrice: 7990,
          isAvailable: true,
        },
        {
          onFire: true,
          brand: "Бренд",
          name: "Полное название товара в несколько строк для вида с обрывом в конце блаблаблабла цузщкзцушкзцщкуз",
          price: 5990,
          oldPrice: 7990,
          isAvailable: true,
        },
        {
          onFire: true,
          brand: "Бренд",
          name: "Полное название товара в несколько строк для вида с обрывом в конце блаблаблабла цузщкзцушкзцщкуз",
          price: 5990,
          oldPrice: 7990,
          isAvailable: true,
        },
        {
          onFire: true,
          brand: "Бренд",
          name: "Полное название товара в несколько строк для вида с обрывом в конце блаблаблабла цузщкзцушкзцщкуз",
          price: 5990,
          oldPrice: 7990,
          isAvailable: true,
        },
        {
          onFire: true,
          brand: "Бренд",
          name: "Полное название товара в несколько строк для вида с обрывом в конце блаблаблабла цузщкзцушкзцщкуз",
          price: 5990,
          oldPrice: 7990,
          isAvailable: true,
        },
        {
          onFire: true,
          brand: "Бренд",
          name: "Полное название товара в несколько строк для вида с обрывом в конце блаблаблабла цузщкзцушкзцщкуз",
          price: 5990,
          oldPrice: 7990,
          isAvailable: true,
        },
      ],
    };
  },
};
</script>

<style croped lang="scss">
.products {
  width: 100%;
  &__wrapper {
    width: 100%;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 24px;
    margin-bottom: 20px;
    @media (max-width: 1230px) {
      grid-template-columns: repeat(3, 1fr);
    }
    @media (max-width: 600px) {
      grid-template-columns: repeat(2, 1fr);
      gap: 12px;
    }
    @media (max-width: 375px) {
      grid-template-columns: 1fr;
    }
  }
  &__title {
    color: rgb(51, 51, 51);
    font-family: PT Sans;
    font-size: 22px;
    font-weight: 400;
    line-height: 28px;
    margin: 12px 0;
    @media (min-width: 950px) {
      display: none;
    }
  }
}
</style>
