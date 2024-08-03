<template>
  <div class="my-input" @click="focusInput">
    <img src="../assets/icons/lupa.svg" alt="search" />
    <label :for="id" class="my-input__label">
      <input
        ref="inputField"
        :id="id"
        :type="type"
        v-model="internalValue"
        @input="handleInput"
        @focus="handleFocus"
        @blur="handleBlur"
        class="my-input__input"
        :placeholder="isFocused ? '' : placeholder"
      />
    </label>
    <div
      v-if="internalValue.length > 0"
      class="my-input__cross"
      @click.stop="clearInput"
    >
      <img src="../assets/icons/cross.svg" alt="X" />
    </div>
    <div v-if="internalValue.length > 0">

      <MyButton text="Найти" />
    </div>
  </div>
</template>

<script>
import MyButton from "./MyButton.vue";
export default {
  name: "MyInput",
  components: {
    MyButton,
  },
  props: {
    value: {
      type: String,
      default: "",
    },
    type: {
      type: String,
      default: "text",
    },
    id: {
      type: String,
      required: true,
    },
    placeholder: {
      type: String,
      default: "",
    },
  },
  data() {
    return {
      internalValue: this.value,
      isFocused: false,
    };
  },
  methods: {
    handleInput(event) {
      this.internalValue = event.target.value;
    },
    focusInput() {
      this.$refs.inputField.focus();
    },
    clearInput() {
      this.internalValue = "";
    },
    handleFocus() {
      this.isFocused = true;
    },
    handleBlur() {
      this.isFocused = false;
    },
  },
  watch: {
    value(newValue) {
      this.internalValue = newValue;
    },
  },
};
</script>

<style lang="scss" scoped>
.my-input {
  gap: 10px;
  display: flex;
  width: 100%;
  margin: 0 24px;
  border-radius: 10px;
  align-items: center;
  padding: 6px 4px 6px 16px;
  min-height: 48px;
  box-sizing: border-box;
  border: 1px solid rgb(170, 170, 170);
  transition: all 0.1s ease-in;
  cursor: text;

  &:hover {
    border: 1px solid var(--color-brand);
  }

  &__label {
    color: rgb(51, 51, 51);
    width: 100%;
  }

  &__input {
    padding: 0;
    width: 100%;
    font-family: Inter;
    font-size: 16px;
    font-weight: 400;
    line-height: 150%;
  }

  &__cross {
    background-color: var(--color-font-main);
    opacity: 0.5;
    width: 20px;
    height: 16px;
    border-radius: 50%;
    flex-wrap: wrap;
    display: flex;
    align-content: center;
    justify-content: center;
    cursor: pointer;

    &:hover {
      opacity: 1;
    }
  }
}
</style>
