<template>
  <button
    @click="$emit('selectOption', this.option)"
    :style="{
      boxShadow: this.currentOption == this.option ? ' inset 0px 0px 0px 5px #FFC700' : 'none',
      background: this.option,
    }"
    class="test-color-button"
  >
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: "test-color-button",
  props: {
    currentOption: {
      type: String,
      requred: true,
    },
    option: {
      type: String,
      requred: true,
    },
  },
};
</script>

<style scoped>
.test-color-button {
  width: 25vw;
  height: 25vw;
  max-width: 200px;
  max-height: 200px;
}
</style>
