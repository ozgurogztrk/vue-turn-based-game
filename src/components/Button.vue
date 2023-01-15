<script lang="ts">
export default {
  props: {
    type: {
      type: String,
      required: true,
    },
    content: {
      type: String,
      required: true,
    },

    isDisabled: {
      type: Boolean,
      default: false,
      required: false,
    },
  },

  methods: {
    onClick() {
      this.$emit("on-click");
    },
  },
};
</script>

<template>
  <button :class="type" @click="onClick()" :disabled="isDisabled">
    {{ content }}
  </button>
</template>

<style scoped lang="scss">
@use "../assets/scss/components/button";
</style>
