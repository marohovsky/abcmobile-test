<template>
  <div @event-burger.stop="toggleNavBar" class="app">
    <transition name="slide-fade">
      <navbar-vue v-if="burgerIsOpen" />
    </transition>

    <router-view></router-view>
  </div>
</template>
<script>
import NavbarVue from "./components/Navbar.vue";
export default {
  components: { NavbarVue },

  data() {
    return {
      burgerIsOpen: false,
    };
  },
  methods: {
    toggleBurger() {
      this.burgerIsOpen = !this.burgerIsOpen;
      if (this.burgerIsOpen) {
        document.body.style.overflow = "hidden";
      } else {
        document.body.style.overflow = "";
      }
    },
  },
};
</script>
<style>
@import url("https://fonts.googleapis.com/css2?family=PT+Serif&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Yeseva+One&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Merriweather&display=swap");

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.app {
}
.text-yellow {
  color: #ffc700;
}
.text-white {
  color: #ffffff;
}

p {
  font-family: "PT Serif", serif;
  font-style: normal;
  font-weight: 400;
}

h3 {
  font-family: "PT Serif", serif;
  font-style: normal;
  font-weight: 400;
  font-size: 18px;
  line-height: 24px;
  text-align: center;
  letter-spacing: 0.05em;
}
.merri {
  font-family: "Merriweather";
  font-style: normal;
  font-weight: 400;
  font-size: 16px;
  line-height: 20px;
  letter-spacing: 0.05em;
}

.merri-bold {
  font-family: "Merriweather";
  font-style: normal;
  font-weight: 700;
  font-size: 15px;
  line-height: 20px;
  text-align: center;
  letter-spacing: 0.05em;
}
h1 {
  font-family: "Yeseva One";
  font-style: normal;
  font-weight: 400;
  font-size: 30px;
  line-height: 35px;
  text-align: center;
  letter-spacing: 0.03em;
  text-transform: uppercase;
}
h2 {
  font-family: "Yeseva One";
  font-size: 18px;
  line-height: 128%;
  text-align: center;
  letter-spacing: 0.05em;
}
button {
  padding: 0;
  border: none;
  font: inherit;
  color: inherit;
  background-color: transparent;
  cursor: pointer;
}
main {
  padding-top: 10vh;
}
.slide-fade-enter-active {
  transition: all 0.8s ease-in-out;
}

.slide-fade-leave-active {
  transition: all 0.8s ease-in-out;
}

.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateX(-100vw);
}
</style>
