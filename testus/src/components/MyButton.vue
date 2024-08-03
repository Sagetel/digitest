<template>
  <button class="my-button">
    {{ text }}
  </button>
</template>
<script>
export default {
  name: "MyButton",
  props: {
    text: {
      type: String,
      required: true,
    },
  },
};
</script>

<style scoped>
.my-button {
  border-radius: 5px;
  background: rgb(115, 151, 245);
  color: white;
  border: none;
  padding: 10px 20px;
  cursor: pointer;
  transition: background-color 0.3s;
  font-family: PT Sans;
  font-size: 16px;
  font-weight: 400;
  line-height: 14px;
}

.my-button:hover {
  background-color: #0056b3;
}
</style>
