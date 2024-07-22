<template>
  <span v-confetti />
  <div class="win-message">Congratulations! You have won the game! 🎉</div>
</template>

<script setup lang="ts">
import { vConfetti } from "@neoconfetti/vue";
</script>

<style scoped>
.win-message {
  font-size: 14px;
  margin: 10px 0;
  color: #fff;
}
</style>
