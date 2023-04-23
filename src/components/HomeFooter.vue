<template lang="">
  <footer>
    <p class="merri top-text">
      Прохождение теста займет у вас не более <span class="text-yellow">12 минут</span>, а его
      результаты вы сможете
      <span class="text-yellow">использовать всю жизнь.</span>
    </p>

    <div class="main-container">
      <img class="lightning-left" src="@/assets/lightning-img.png" alt="lightning img" />
      <img class="lightning-right" src="@/assets/lightning-img.png" alt="lightning img" />
      <p class="merri">
        Профессиональная интерпретация и детально <span>проработанные рекомендации</span> позволят
        вам качественно <span>изменить все аспекты своей жизни</span>: от финансового до любовного.
      </p>
    </div>
    <main-button
      @click="$router.push('/iq-test')"
      style="margin: 0 auto; border: 1px solid white; background: inherit; color: white"
      >пройти тест</main-button
    >
    <div class="copyright-container">
      <img class="copyright" src="@/assets/copyright.svg" alt="" />
    </div>
  </footer>
</template>
<style scoped>
footer {
  display: flex;
  position: relative;
  flex-direction: column;
  gap: 20px;
  padding: 3em 1em;
  background: url("@/assets/rain-bk.png");
}
.lightning-left {
  position: absolute;
  left: 0;
  bottom: 1em;
}
.lightning-right {
  position: absolute;
  transform: scaleX(-1);
  right: 0;
  top: 1em;
}
.top-text {
  width: 80%;
  color: #ffff;
}
span {
  font-weight: 600;
}
.main-container {
  padding: 2em 1em;
  background: rgba(243, 243, 242, 0.8);
  border-radius: 20px;
}
.copyright-container {
  position: absolute;
  width: 100%;
  left: 0;
  bottom: 10px;
}
.copyright-container img {
  display: block;
  margin: 0 auto;
  width: 50px;
  height: 18px;
}
</style>
