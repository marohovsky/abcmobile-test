<template>
  <section>
    <h1>Ваш результат рассчитан:</h1>
    <p>
      <u>Вы относитесь к 3% респондентов</u>, чей уровень интеллекта более чем на 15 пунктов
      отличается от среднего в большую или меньшую сторону!
    </p>
    <h2>Скорее получите свой результат!</h2>
    <div class="info-wrapper">
      <div class="info">
        В целях защиты персональных данных результат теста, их подробная интерпретация и
        рекомендации доступны в виде голосового сообщения по звонку с вашего мобильного телефона
      </div>
      <span>Звоните скорее, запись доступна всего </span>
      <span>{{ remainingTime() }} минут</span>
    </div>
    <div class="call-wrapper">
      <img class="lightning-left" src="@/assets/lightning-img.png" alt="" />
      <img class="lightning-right" src="@/assets/lightning-img.png" alt="" />
      <button @click="getData" class="call">
        <img src="@/assets/call.svg" alt="phone logo" />
        Позвонить и прослушать результат
      </button>
    </div>

    <transition name="fade">
      <div v-if="dataFromAPI">
        <ul>
          <li v-for="(value, key) in dataFromAPI" :key="key">
            <span>{{ key }}</span> : {{ value }}
          </li>
        </ul>
      </div>
    </transition>
    <p class="disclaimer">
      TERMENI SI CONDITII: ACESTA ESTE UN SERVICIU DE DIVERTISMENT. PRIN FOLOSIREA LUI DECLARATI CA
      AVETI 18 ANI IMPLINITI,
    </p>
  </section>
</template>
<script>
export default {
  data() {
    return {
      countdown: 600,
      dataFromAPI: "",
    };
  },
  methods: {
    getData() {
      fetch("https://swapi.dev/api/people/1/")
        .then((response) => {
          return response.json();
        })
        .then((data) => {
          this.dataFromAPI = data;
        });
    },
    startCountdown() {
      setInterval(() => {
        this.countdown--;
      }, 1000);
    },
    remainingTime() {
      const minutes = Math.floor(this.countdown / 60);
      const seconds = this.countdown % 60;
      return `${minutes < 10 ? "0" : ""}${minutes}:${seconds < 10 ? "0" : ""}${seconds}`;
    },
  },
  created() {
    this.startCountdown();
  },
};
</script>
<style scoped>
section {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;
  padding: 1em;
  padding-bottom: 5em;
}
.lightning-left {
  position: absolute;
  left: -1em;

  z-index: 20;
}
.lightning-right {
  position: absolute;
  right: -1em;
  transform: scale(-1, -1);
  top: -2em;
  z-index: 20;
}
ul {
  padding: 1em;
  font-weight: 500;
  list-style: none;
  color: #ffffff;
}
ul span {
  font-weight: 700;
  color: #3bde7c;
}
h1 {
  font-family: "PT Serif";
  font-style: normal;
  font-weight: 700;
  font-size: 17px;
  line-height: 16px;
  text-align: center;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: #ffffff;
}
p {
  font-family: "PT Serif";
  font-style: normal;
  font-weight: 400;
  font-size: 15px;
  line-height: 18px;
  text-align: center;
  color: #ffffff;
}
h2 {
  font-family: "PT Serif";
  font-style: normal;
  font-weight: 700;
  font-size: 18px;
  line-height: 22px;
  text-align: center;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: #3bde7c;
}
.info-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  color: #3bde7c;
}
.info {
  padding: 2em;
  background: #1c2741;
  font-family: "Roboto";
  font-style: normal;
  font-weight: 500;
  font-size: 8px;
  line-height: 14px;
  text-align: center;
  letter-spacing: 2px;
  text-transform: uppercase;
  color: #ffffff;
}
.call-wrapper {
  position: relative;
}
.call {
  display: flex;
  gap: 10px;
  background: #eb1b00;
  padding: 2em 1em;
  border-radius: 5px;
  font-family: "Roboto";
  font-style: normal;
  font-weight: 900;
  font-size: 15px;
  line-height: 18px;
  letter-spacing: 0.05em;
  color: #ffffff;
  z-index: 40;
}
.disclaimer {
  position: fixed;
  bottom: 0;
  padding: 1em;
  padding-top: 3em;
  height: 5em;
  overflow: auto;
}
.fade-enter-active {
  transition: opacity 0.5s ease;
}
.fade-leave-active {
  transition: opacity 0.5s ease;
}

.fade-enter-from {
  opacity: 0;
}
.fade-leave-to {
  opacity: 0;
}
</style>
