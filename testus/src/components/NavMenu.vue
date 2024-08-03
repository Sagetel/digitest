<template>
  <nav class="nav-menu">
    <ul>
      <li v-for="(item, index) in items" :key="index">
        <a :href="item.href">{{ item.label }}</a>
      </li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: "NavMenu",
  props: {
    items: {
      type: Array,
      required: true,
      default: () => [],
    },
  },
};
</script>

<style scoped lang="scss">
.nav-menu {
  margin-right: 28px;
  ul {
    display: flex;
    gap: 20px;
  }
  li {
    a {
      color: rgb(57, 57, 57);
      white-space: nowrap;
      font-family: Inter;
      font-size: 14px;
      font-weight: 400;
      transition: color 0.15s ease-in;
      &:hover {
        color: var(--color-font-hover);
      }
    }
  }
}
</style>
