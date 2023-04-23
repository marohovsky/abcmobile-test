<template>
  <header>
    <button @click="$root.toggleBurger()">
      <img src="../assets/burger-logo.svg" alt="burger logo" />
    </button>
    <div v-if="title">
      <img class="logo" src="@/assets/brain-img.png" alt="brain logo" />
      <h1 class="text-yellow">{{ title }}</h1>
    </div>
  </header>
</template>
<script>
export default {
  props: {
    title: {
      type: String,
    },
  },
};
</script>
<style scoped>
header {
  position: fixed;
  top: 0;
  width: 100%;
  height: 10vh;
  z-index: 30;
  display: flex;
  gap: 20px;
  align-items: center;
  background: #181818;
  padding: 15px;
}
div {
  display: flex;
  gap: 20px;
  align-items: center;
}
.logo {
  width: 7vh;
  height: 7vh;
}
h1 {
  font-family: "Yeseva One";
  font-style: normal;
  font-weight: 400;
  font-size: 16px;
  line-height: 14px;
  letter-spacing: 0.05em;
}
</style>
