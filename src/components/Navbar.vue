<template>
  <nav>
    <ul>
      <li @click="linkTo('/')">Главная</li>
      <li @click="linkTo('/', 'quoteRef')">Информация о тесте</li>
      <li @click="linkTo('/iq-test')" class="text-yellow">Пройти тест</li>
    </ul>
    <button @click="$root.toggleBurger()" class="close">
      <img src="@/assets/burger-close-logo.svg" alt="close button" />
    </button>
  </nav>
</template>
<script>
export default {
  methods: {
    linkTo(route, ref) {
      this.$router.push(route);
      this.$root.toggleBurger();
      if (ref) {
        setTimeout(() => {
          const refElement = document.getElementById("quoteRef");
          refElement.scrollIntoView({ behavior: "smooth" });
        }, 1000);
      }
    },
  },
};
</script>
<style scoped>
nav {
  position: fixed;
  left: 0;
  top: 0;
  z-index: 60;
  width: 100%;
  background: #181818;
  height: 100%;
}
.close {
  position: absolute;
  top: 2em;
  right: 2em;
  z-index: 70;
}
ul {
  padding: 6em 2em;
  font-weight: 500;
  list-style: none;
  color: #ffffff;
}
li {
  margin-bottom: 27px;
  font-family: "Roboto";
  font-style: normal;
  font-weight: 500;
  font-size: 16px;
  line-height: 22px;
  cursor: pointer;
  text-transform: uppercase;
}
</style>
