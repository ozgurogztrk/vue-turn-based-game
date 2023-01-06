<script lang="ts">
export default {
  props: {
    owner: {
      type: String,
      required: true,
    },
    health: {
      type: Number,
      required: true,
    },
    title: {
      type: String,
      required: false,
    },
  },

  computed: {
    customStyling() {
      return [{ width: `${this.health}%` }];
    },
  },
};
</script>

<template>
  <div class="container column align-center text-center justify-center">
    <h2>{{ title }}</h2>
    <div class="health-bar">
      <div :class="owner" :style="customStyling">{{ health }}</div>
    </div>
  </div>
</template>

<style scoped lang="scss">
@use "../assets/scss/components/healthBar";
</style>
