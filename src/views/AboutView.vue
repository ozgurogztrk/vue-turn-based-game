<script lang="ts">
import Button from "../components/Button.vue";
import { RouterLink } from "vue-router";

export default {
  components: { Button, RouterLink },
};
</script>

<template>
  <div class="container bg-default align-center justify-center">
    <p>
      A small game inspired by some of the projects from
      <strong> Kablosuz Kedi(Gökhan Kandemir)</strong>'s Vue.js course.
    </p>
  </div>

  <div class="container bg-default align-center justify-center">
    <RouterLink to="/"><Button type="primary" content="Go Back" /></RouterLink>
  </div>
</template>

<style scoped lang="scss">
@use "../assets/scss/layouts/about";
</style>
