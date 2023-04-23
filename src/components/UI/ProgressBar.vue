<template>
  <div class="progress-bar-body">
    <div
      :style="{ width: (progress.current / progress.total) * 100 + '%' }"
      class="progress-bar"
    ></div>
  </div>
</template>
<script>
export default {
  name: "progress-bar",
  props: {
    progress: {
      type: Object,
      requred: true,
    },
  },
};
</script>
<style scoped>
.progress-bar-body {
  width: 100%;
  height: 1em;
  background: #f2f3f3;
  border-radius: 20px;
}
.progress-bar {
  height: 100%;
  background: #3bde7c;
  border-radius: 20px;
  transition: width 1s ease;
}
</style>
