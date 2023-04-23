<template>
  <main-headerVue />
  <main>
    <home-title-vue />
    <home-body-vue />
  </main>
  <home-footer-vue />
</template>

<script>
import MainHeaderVue from "@/components/MainHeader.vue";
import HomeTitleVue from "@/components/HomeTitle.vue";
import HomeBodyVue from "@/components/HomeBody.vue";
import HomeFooterVue from "@/components/HomeFooter.vue";

export default {
  name: "HomeView",
  components: {
    MainHeaderVue,
    HomeTitleVue,
    HomeBodyVue,
    HomeFooterVue,
  },
};
</script>
<style scoped></style>
