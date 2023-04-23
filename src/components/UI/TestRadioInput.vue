<template>
  <input :checked="currentOption === option" type="radio" :id="option" />
  <label @click="$emit('selectOption', this.option)" :for="option">
    <div></div>
    <span><slot></slot></span>
  </label>
</template>

<script>
export default {
  name: "test-radio-input",
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
input {
  height: 0px;
  width: 0px;
  visibility: hidden;
}
div {
  min-width: 20px;
  height: 20px;
  border: 1px solid #ffff;
  border-radius: 100px;
}
label {
  display: flex;
  align-items: center;
  justify-content: flex-start;
  width: 100%;
  cursor: pointer;
  padding: 10px 0;
  padding-left: 20px;
  gap: 20px;
  background: #f2f3f344;
}
span {
  font-family: "PT Serif";
  font-style: normal;
  font-weight: 400;
  font-size: 18px;
  letter-spacing: 0.05em;
  color: #fff;
}
input:checked + label div {
  background: blue;
  border: 1px solid #272727;
}
input:checked + label {
  background: #ffc700;
}
input:checked + label span {
  color: #272727;
}
</style>
