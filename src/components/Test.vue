<template>
  <section>
    <h1>{{ capitalizedText(test.title) }}</h1>
    <img v-if="test.img" :src="imageUrl" alt="test img" />
    <div v-if="test.type === 'buttons'" class="buttons-answer">
      <test-button
        v-for="option in options"
        :option="option"
        :currentOption="this.selectedOption"
        :key="option"
        @selectOption="setSelectOption"
        >{{ capitalizedText(option) }}</test-button
      >
    </div>
    <div v-if="test.type === 'radio-inputs'" class="radio-inputs">
      <test-radio-input
        v-for="option in options"
        :option="option"
        :currentOption="this.selectedOption"
        :key="option"
        @selectOption="setSelectOption"
        >{{ capitalizedText(option) }}</test-radio-input
      >
    </div>
    <div v-if="test.type === 'color-buttons'" class="color-buttons">
      <test-color-button
        v-for="option in options"
        :option="option"
        :currentOption="this.selectedOption"
        :key="option"
        @selectOption="setSelectOption"
      />
    </div>
    <main-button :disabled="!selectedOption" @click="sendOption">Далее</main-button>
  </section>
</template>
<script>
export default {
  props: {
    test: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      selectedOption: "",
      options: [],
    };
  },
  emits: ["selectOption"],
  methods: {
    capitalizedText(text) {
      return text.charAt(0).toUpperCase() + text.slice(1).toLowerCase();
    },
    setSelectOption(newOption) {
      this.selectedOption = newOption;
    },
    shuffleOptions(options) {
      for (let i = options.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [options[i], options[j]] = [options[j], options[i]];
      }
      return options;
    },
    sendOption() {
      this.$emit("addAnswer", this.selectedOption);
      this.selectedOption = "";
    },
  },
  created() {
    if (this.test.isShufleOptions) {
      this.options = this.shuffleOptions(this.test.options);
    } else {
      this.options = [...this.test.options];
    }
  },
  watch: {
    test: function () {
      if (this.test.isShufleOptions) {
        this.options = this.shuffleOptions(this.test.options);
      } else {
        this.options = [...this.test.options];
      }
    },
  },
  computed: {
    imageUrl() {
      return require(`@/assets/test-iq/${this.test.img}`);
    },
  },
};
</script>
<style scoped>
section {
  display: flex;
  height: 100%;
  width: 100%;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  gap: 20px;
}
h1 {
  font-family: "PT Serif";
  font-style: normal;
  color: #ffffff;
  font-weight: 400;
  font-size: 20px;
  line-height: 26px;
  text-align: center;
  letter-spacing: 0.05em;
  text-transform: none;
}
.buttons-answer {
  display: flex;
  width: 100%;
  align-items: center;
  justify-content: space-around;
}
.radio-inputs {
  display: flex;
  flex-direction: column;
  width: 100%;
  gap: 10px;
  align-items: center;
  justify-content: space-around;
}
.color-buttons {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 20px;
  flex-wrap: wrap;
  width: 100%;
}
</style>
