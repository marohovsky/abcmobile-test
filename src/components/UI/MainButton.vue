<template>
  <button class="btn">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: "main-button",
};
</script>

<style scoped>
.btn {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 1em;
  width: 180px;
  height: 41px;
  font-weight: 700;
  font-size: 14px;
  line-height: 18px;
  text-align: center;
  letter-spacing: 0.1em;
  background: #ffc700;
  color: #0d0c11;
  text-transform: uppercase;
  border-radius: 100px;
}
.btn:disabled {
  cursor: inherit;
  background: #dadada;
  color: #8e8e8e;
  box-shadow: inset 0px 4px 10px rgba(0, 0, 0, 0.25);
}
</style>
