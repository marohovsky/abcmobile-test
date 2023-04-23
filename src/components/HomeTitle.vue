<template>
  <section class="home-title">
    <h3 class="text-white">Пройдите точный и быстрый</h3>
    <div class="title-center">
      <h1 class="text-yellow">тест на определение IQ</h1>
      <img class="brain-img" src="@/assets/brain-img.png" alt="brain img" />
    </div>
    <main-button @click="$router.push('/iq-test')">пРойти тест</main-button>
    <div class="title-footer">
      <span class="text-yellow merri-bold"
        >и получите рекомендации по развитию своего интеллекта</span
      >
      <span class="text-white merri-bold"
        >и улучшению финансового благосостояния и личной жизни</span
      >
    </div>
    <button class="title-btn">
      <img class="arrow-top" src="@/assets/arrow-top.svg" alt="arrow-top" />
      <p class="text-white">Подробнее</p>
    </button>
  </section>
</template>

<style scoped>
.home-title {
  display: flex;
  position: relative;
  gap: 22px;
  padding: 1em;
  width: 100%;
  height: 80vh;
  text-align: center;
  flex-direction: column;
  align-items: center;
  background-image: url("@/assets/rain-bk.png");
}
.title-center {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 70%;
}
.title-footer {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.title-btn {
  display: flex;
  flex-direction: column;
  align-items: center;
  position: absolute;
  bottom: 0;
}
.brain-img {
  width: 40vw;
  height: 40vw;
  max-width: 200px;
  max-height: 200px;
  filter: drop-shadow(0px 0px 60px #005fc0);
}
.arrow-top {
  margin-top: 15px;
  padding: 5px;
  display: block;
  background: white;
  border-radius: 100px;
}
</style>
