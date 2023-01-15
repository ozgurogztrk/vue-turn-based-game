<script lang="ts">
import Button from "../components/Button.vue";
import HealthBar from "../components/HealthBar.vue";
import { RouterLink, RouterView } from "vue-router";

export default {
  components: {
    Button,
    HealthBar,
    RouterLink,
    RouterView,
  },

  data() {
    return {
      showButtonGroup: false,
      playerHealth: 100,
      enemyHealth: 100,
    };
  },

  methods: {
    showButtons() {
      this.showButtonGroup = !this.showButtonGroup;
    },

    attack(minDamage: number, maxDamage: number) {
      this.enemyHealth -= Math.floor(Math.random() * maxDamage + minDamage);
      this.playerHealth -= Math.floor(Math.random() * 20 + 5);
      this.gameState();
    },

    heal() {
      this.playerHealth = 100;
      this.playerHealth -= Math.floor(Math.random() * 20 + 5);
    },

    gameState() {
      if (this.playerHealth <= 0) {
        window.alert("The enemy has won!");
        this.quit();
      } else if (this.enemyHealth <= 0) {
        window.alert("You have won!");
        this.quit();
      }
    },

    quit() {
      this.playerHealth = 100;
      this.enemyHealth = 100;
      this.showButtons();
    },
  },
};
</script>

<template>
  <main class="flex flex-column align-center justify-center">
    <div class="flex flex-wrap align-center justify-center card card-main">
      <HealthBar owner="player" :health="playerHealth" title="Player" />
      <HealthBar owner="enemy" :health="enemyHealth" title="Enemy" />
    </div>

    <div class="flex flex-wrap gap-column align-center justify-center card">
      <Button
        type="primary"
        content="Play"
        v-show="!showButtonGroup"
        @on-click="showButtons"
      />
      <RouterLink to="/about">
        <Button type="primary" content="About" v-show="!showButtonGroup"
      /></RouterLink>

      <div
        class="flex flex-wrap align-center justify-center gap w-100"
        v-show="showButtonGroup"
      >
        <Button type="primary" content="Attack" @on-click="attack(5, 20)" />
        <Button
          type="warning"
          content="Special Ability"
          @on-click="attack(10, 30)"
        />
        <Button type="success" content="Heal" @on-click="heal()" />
        <Button type="danger" content="Quit" @on-click="quit()" />
      </div>
    </div>
  </main>
</template>
