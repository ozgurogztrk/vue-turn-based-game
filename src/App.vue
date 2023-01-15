<script lang="ts">
import { RouterLink, RouterView } from "vue-router";
import TheHeader from "./components/TheHeader.vue";

export default {
  components: {
    RouterView,
    TheHeader,
  },
};
</script>

<template>
  <TheHeader />

  <Transition>
    <RouterView />
  </Transition>
</template>
