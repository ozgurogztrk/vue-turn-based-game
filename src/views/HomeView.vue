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
      buttonDisabled: false,
    };
  },

  methods: {
    showButtons() {
      this.showButtonGroup = !this.showButtonGroup;
    },

    attack(minDamage: number, maxDamage: number) {
      this.buttonDisabled = true;
      this.enemyHealth -= Math.floor(Math.random() * maxDamage + minDamage);

      setTimeout(() => {
        this.buttonDisabled = false;
        this.playerHealth -= Math.floor(Math.random() * 20 + 5);
      }, 1000);

      this.gameState();
    },

    heal() {
      this.buttonDisabled = true;
      this.playerHealth = 100;

      setTimeout(() => {
        this.buttonDisabled = false;
        this.playerHealth -= Math.floor(Math.random() * 25 + 10);
      }, 1000);
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
        <Button
          type="primary"
          content="Attack"
          @on-click="attack(5, 20)"
          :isDisabled="buttonDisabled"
        />
        <Button
          type="warning"
          content="Special Ability"
          @on-click="attack(10, 30)"
          :isDisabled="buttonDisabled"
        />
        <Button
          type="success"
          content="Heal"
          @on-click="heal()"
          :isDisabled="buttonDisabled"
        />
        <Button
          type="danger"
          content="Quit"
          @on-click="quit()"
          :isDisabled="buttonDisabled"
        />
      </div>
    </div>
  </main>
</template>
