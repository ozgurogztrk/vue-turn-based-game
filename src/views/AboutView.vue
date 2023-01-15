<script lang="ts">
import Button from "../components/Button.vue";
import { RouterLink } from "vue-router";

export default {
  components: { Button, RouterLink },
};
</script>

<template>
  <section class="flex flex-column align-center justify-center">
    <div
      class="flex flex-wrap align-center justify-center text-center card card-main"
    >
      <p>
        A small game inspired by some of the projects from
        <strong> Kablosuz Kedi(Gökhan Kandemir)</strong>'s Vue.js course.
      </p>
    </div>

    <div class="flex flex-wrap align-center justify-center card">
      <RouterLink to="/"
        ><Button type="primary" content="Go Back"
      /></RouterLink>
    </div>
  </section>
</template>

<style scoped lang="scss">
@use "../assets/scss/layouts/about";
</style>
