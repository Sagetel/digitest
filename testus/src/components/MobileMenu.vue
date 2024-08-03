<template>
    <div class="mobile" @click="handleOutsideClick">
      <div class="mobile__content" ref="mobileContent">
        <FilterPanel />
      </div>
    </div>
  </template>
  
  <script>
  import FilterPanel from "./FilterPanel.vue";
  export default {
    components: {
      FilterPanel,
    },
    props: {
      closeMenu: {
        type: Function,
        required: true,
      },
    },
    methods: {
      handleOutsideClick(event) {
        if (!this.$refs.mobileContent.contains(event.target)) {
          this.closeMenu();
        }
      },
    },
    mounted() {
      document.addEventListener("click", this.handleOutsideClick);
    },
    beforeDestroy() {
      document.removeEventListener("click", this.handleOutsideClick);
    },
  };
  </script>
  
  <style lang="scss">
  .mobile {
    position: absolute;
    top: 0px;
    left: 0px;
    right: 0px;
    background-color: #7398f55e;
    z-index: 10;
    height: 100%;
    display: flex;
    justify-content: center;
    backdrop-filter: blur(2px);
    @media (min-width: 960px) {
      display: none;
    }
    &__content {
      margin-top: 20px;
      background-color: white;
      padding: 10px;
      height: fit-content;
      border-radius: 5px;
    }
  }
  </style>
  