<template>
  <main-header-vue :title="titleInHeaader" />
  <main>
    <div v-if="titleInHeaader !== 'Готово!'" class="progress-bar-wrapper">
      <progress-bar v-bind:progress="{ current: this.currentTest, total: this.tests.length }" />
    </div>
    <div v-if="currentTest < tests.length" class="test-container">
      <test-vue @addAnswer="setAnswer" :test="tests[currentTest]" />
    </div>
    <div v-if="loading" class="loading">
      <h1>обработка результатов</h1>
      <img style="width: 20vw; height: 20vh" src="@/assets/spin.svg" alt="" />
      <p>
        Определение стиля мышления........... ....
        ...................................................
      </p>
    </div>
    <div v-if="titleInHeaader === 'Готово!'">
      <test-result />
    </div>
  </main>
</template>
<script>
import MainHeaderVue from "@/components/MainHeader.vue";
import TestVue from "@/components/Test.vue";
import TestResult from "@/components/TestResult.vue";

export default {
  components: { MainHeaderVue, TestVue, TestResult },
  data() {
    return {
      loading: false,
      titleInHeaader: "Тест на определение IQ",
      testAnswers: [],
      currentTest: 0,
      tests: [
        { title: "ваш пол:", img: "", options: ["мужчина", "женщина"], type: "radio-inputs" },
        {
          title: "укажите ваш возраст:",
          img: "",
          options: ["До 18", "От 18 до 28", "от 29 до 35", "От 36"],
          type: "radio-inputs",
        },
        {
          title: "Выберите лишнее:",
          img: "",
          options: ["Дом", "Шалаш", "Бунгало", "Скамейка", "Хижина"],
          type: "radio-inputs",
        },
        {
          title: "Продолжите числовой ряд: 18  20  24  32  ",
          img: "",
          options: ["62", "48", "74", "57", "60", "77"],
          type: "radio-inputs",
        },
        {
          title: "Выберите цвет, который сейчас наиболее Вам приятен:",
          img: "",
          options: [
            "#A8A8A8",
            "#0000A9",
            "#00A701",
            "#F60100",
            "#FDFF19",
            "#A95403",
            "#000000",
            "#850068",
            "#46B2AC",
          ],
          type: "color-buttons",
        },
        {
          title:
            "Отдохните пару секунд, еще раз Выберите цвет, который сейчас наиболее Вам приятен:",
          img: "",
          options: [
            "#A8A8A8",
            "#0000A9",
            "#00A701",
            "#F60100",
            "#FDFF19",
            "#A95403",
            "#000000",
            "#850068",
            "#46B2AC",
          ],
          type: "color-buttons",
          isShufleOptions: true,
        },
        {
          title: "Какой из городов лишний?",
          img: "",
          options: ["Вашингтон", "Лондон", "Париж", "Нью-Йорк ", "Москва", "Оттава"],
          type: "radio-inputs",
          isShufleOptions: true,
        },
        {
          title: "Выберите правильную фигуру из четырёх пронумерованных.",
          img: "figure-test-img.png",
          options: ["1", "2", "3", "4"],
          type: "buttons",
        },
        {
          title: "Вам привычнее и важнее:",
          img: "",
          options: [
            "Наслаждаться каждой минутой проведенного времени",
            "Быть устремленными мыслями в будущее",
            "Учитывать в ежедневной практике прошлый опыт",
          ],
          type: "radio-inputs",
        },
        {
          title:
            "Какое определение, по-Вашему, больше подходит к этому геометрическому изображению: ",
          img: "tetrahedron-test-img.png",
          options: ["оно остроконечное", "оно устойчиво", "оно-находится в состоянии равновесия"],
          type: "radio-inputs",
        },
        {
          title: "Вставьте подходящее число",
          img: "star-test-img.png",
          options: ["34", "36", "53", "44", "66", "42"],
          type: "buttons",
        },
        {
          title: "Вставьте подходящее число",
          img: "star-test-img.png",
          options: ["34", "36", "53", "44", "66", "42"],
          type: "buttons",
          isShufleOptions: true,
        },
      ],
    };
  },
  methods: {
    setAnswer(answer) {
      this.testAnswers = [...this.testAnswers, answer];
      if (this.currentTest < this.tests.length) {
        this.currentTest = this.currentTest + 1;
      }
    },
    getResult() {
      this.loading = false;
      this.titleInHeaader = "Готово!";
    },
  },
  watch: {
    currentTest: function () {
      if (this.currentTest === this.tests.length) {
        this.loading = true;
        setTimeout(this.getResult, 2000);
      }
    },
  },
};
</script>
<style scoped>
header {
  position: relative;
}
.progress-bar-wrapper {
  width: 90%;
}
main {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;
  min-height: 90vh;
  padding: 1em;
  background: url("@/assets/rain-bk.png");
}
.test-container {
  height: 80vh;
  width: 100%;
}
.loading {
  display: flex;
  flex-direction: column;
  align-items: center;
}
h1 {
  font-family: "PT Serif";
  font-style: normal;
  padding: 0 2em;
  padding-top: 2em;
  font-weight: 400;
  font-size: 23px;
  line-height: 30px;
  text-align: center;
  letter-spacing: 0.05em;
  color: #ffff;
}
p {
  font-family: "PT Serif";
  font-style: normal;
  font-weight: 400;
  font-size: 16px;
  line-height: 19px;
  letter-spacing: 0.05em;
  color: #ffff;
}
</style>
