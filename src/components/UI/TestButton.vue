<template>
  <button
    @click="$emit('selectOption', this.option)"
    :style="{
      boxShadow: this.currentOption == this.option ? ' inset 0px 0px 0px 5px #FFC700' : 'none',
    }"
    class="test-btn"
  >
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: "test-button",
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
.test-btn {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 42px;
  height: 42px;
  font-family: "PT Serif";
  font-style: normal;
  font-weight: 400;
  font-size: 20px;
  line-height: 49px;
  text-align: center;
  background: #ffff;
  color: #0d0c11;
}
</style>
