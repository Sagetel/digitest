<template>
  <div>
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

[class*="__container"] {
  max-width: 1720px;
  padding: 0 20px;
  margin: 0 auto;
}
</style>
