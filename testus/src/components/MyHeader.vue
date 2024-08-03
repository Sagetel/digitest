!
<template>
  <header class="header">
    <div class="header__container">
      <div class="header__logo">
        <img class="header__icon" src="../assets/header-logo.svg" alt="logo" />
        <span class="header__title">Логотип</span>
      </div>
      <div class="header__catalog">Каталог</div>
      <MyInput
        v-model="query"
        id="query"
        placeholder="Поиск по 100 000 товаров "
      />
      <NavMenu :items="menuItems" />
    </div>
  </header>
</template>

<script>
import MyInput from "./MyInput.vue";
import NavMenu from "./NavMenu.vue";
export default {
  name: "MyHeader",
  components: {
    MyInput,
    NavMenu,
  },
  data() {
    return {
      query: "",
      menuItems: [
        { label: "Информация о компании", href: "/about" },
        { label: "Контакты", href: "/contacts" },
        { label: "Полезные ссылки", href: "/faq" },
      ],
    };
  },
};
</script>
<style scoped lang="scss">
.header {
  display: flex;
  justify-content: space-between;
  padding: 12px 0;
  font-family: Inter;
  &__container {
    display: flex;
    align-items: center;
    width: 100%;
  }
  &__logo {
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 0 24px;
  }
  &__icon {
    margin-right: 11px;
  }
  &__title {
    font-size: 16px;
  }
  &__catalog {
    display: flex;
    align-items: center;
    justify-content: center;
    box-sizing: border-box;
    margin-left: 8px;
    border: 1px solid var(--color-brand);
    border-radius: 8px;
    padding: 0 24px;
    height: 100%;
    font-family: Inter;
    font-size: 14px;
    font-weight: 500;
    line-height: 17px;
  }
}
</style>
