<script lang="ts">
import { RouterLink, RouterView } from "vue-router";
import TheHeader from "./components/TheHeader.vue";

export default {
  components: {
    RouterLink,
    RouterView,
    TheHeader,
  },
};
</script>

<template>
  <TheHeader />
  <!-- <RouterLink to="/about">About</RouterLink> -->
  <RouterView />
</template>

<style scoped></style>
