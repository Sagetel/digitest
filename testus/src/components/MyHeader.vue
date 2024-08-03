<template>
  <div>
    <header class="header">
      <div class="header__container">
        <div class="header__logo">
          <img class="header__icon" src="../assets/header-logo.svg" alt="logo" />
          <span class="header__title">Логотип</span>
        </div>
        <div class="header__catalog">Каталог</div>
        <div class="header__mobile-menu" @click="toggleMobileMenu($event)">
          <img src="../assets/icons/strelka.svg" alt="menu icon" />
        </div>
        <MyInput v-model="query" id="query" placeholder="Поиск по 100 000 товаров" />
        <div class="header__menu">
          <NavMenu :items="menuItems" />
        </div>
      </div>
    </header>
    <MobileMenu v-if="isMobileMenuOpen" :closeMenu="toggleMobileMenu" />
  </div>
</template>

<script>
import MyInput from "./MyInput.vue";
import NavMenu from "./NavMenu.vue";
import MobileMenu from "./MobileMenu.vue";

export default {
  name: "MyHeader",
  components: {
    MyInput,
    NavMenu,
    MobileMenu,
  },
  data() {
    return {
      query: "",
      menuItems: [
        { label: "Информация о компании", href: "/about" },
        { label: "Контакты", href: "/contacts" },
        { label: "Полезные ссылки", href: "/faq" },
      ],
      isMobileMenuOpen: false,
    };
  },
  methods: {
    toggleMobileMenu(event) {
      if (event) {
        event.stopPropagation();
        event.preventDefault();
      }
      this.isMobileMenuOpen = !this.isMobileMenuOpen;
    },
  },
};
</script>

<style scoped lang="scss">
.header {
  display: flex;
  justify-content: space-between;
  padding: 12px 0;
  font-family: Inter;
  @media (max-width: 950px) {
    padding: 12px 0 0 0;
  }
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
  &__mobile-menu {
    margin-right: 16px;
    cursor: pointer;
    @media (min-width: 950px) {
      display: none;
    }
  }
  @media (max-width: 950px) {
    .header__logo,
    .header__catalog,
    .header__menu {
      display: none;
    }
  }
}
</style>
