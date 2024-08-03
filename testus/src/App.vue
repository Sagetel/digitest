<template>
  <div class="wrapper">
    <MyHeader />
    <MainContent />
  </div>
</template>

<script>
import MyHeader from "./components/MyHeader.vue";
import MainContent from "./components/MainContent.vue";
export default {
  name: "App",
  components: {
    
    MainContent,
    MyHeader,
  },
};
</script>

<style lang="scss">
@import "./main.scss";
.wrapper {
  position: relative;
}

[class*="__container"] {
  max-width: 1720px;
  padding: 0 20px;
  margin: 0 auto;
  @media (max-width: 600px) {
    padding: 0 16px;
  }
}
</style>
