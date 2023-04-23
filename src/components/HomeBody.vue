<template>
  <section id="quoteRef" class="home-body">
    <div class="body-qoute">
      <img class="qoute-bg" src="@/assets/quote-bg.png" alt="" />
      <img src="@/assets/quote-mark.svg" alt="quote-mark" class="open-qoute-mark" />
      <h2 class="text-white">
        Профессиональный IQ-тест позволяет не только определить коэффициент вашего интеллекта, но и
        выработать список рекомендаций для повышения этого показателя.
      </h2>
      <img src="@/assets/quote-mark.svg" alt="quote-mark" class="close-qoute-mark" />
    </div>
    <div class="body-info">
      <p>
        Также по результатам теста <span>вы получите</span> подробные <span>советы</span> по
        определению наиболее перспективной <span>для вашего типа</span>
        <span class="lower-text">интеллекта</span>
        <span>сферы деятельности</span>, которая принесет вам скорейший финансовый результат.
      </p>
      <img src="@/assets/brain-diagram-img.png" alt="brain diagram image" />
      <main-button @click="$router.push('/iq-test')" style="margin-top: -35px"
        >пойти тест</main-button
      >
    </div>
  </section>
</template>
<script></script>
<style scoped>
.home-body {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.body-qoute {
  display: flex;
  position: relative;
  width: 100%;
  padding: 6em 3em;
  background: radial-gradient(
    84.34% 50.29% at 48.75% 49.71%,
    #2950c2 0%,
    rgba(38, 91, 199, 0.96) 40.62%,
    rgba(39, 98, 187, 0) 85.42%
  );
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.qoute-bg {
  position: absolute;
  top: 0;
  left: 0;
  z-index: -1;
  width: 100%;
  height: 100%;
  object-fit: cover;
}
.open-qoute-mark {
  position: absolute;
  top: 3em;
  left: 2em;
}
.close-qoute-mark {
  position: absolute;
  transform: scale(-1, -1);
  bottom: 3em;
  right: 2em;
}
.body-info {
  display: flex;
  width: 100%;
  gap: 20px;
  flex-direction: column;
  align-items: center;
  padding: 3em 1em;
}
p {
  font-size: 16px;
  line-height: 24px;
  letter-spacing: 0.05em;
  color: #272727;
}
span {
  font-weight: 600;
  text-transform: uppercase;
}
span + span::before {
  content: " ";
}
.lower-text {
  text-transform: lowercase;
}
</style>
