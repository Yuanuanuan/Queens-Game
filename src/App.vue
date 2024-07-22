<template>
  <AppSection>
    <GameHeader />
    <GameBoard />
  </AppSection>

  <AppSection>
    <GameInstructions />
  </AppSection>
</template>

<script setup lang="ts">
import AppSection from "@/components/AppSection.vue";
import GameHeader from "@/components/GameHeader.vue";
import GameBoard from "@/components/GameBoard.vue";
import GameInstructions from "@/components/GameInstructions.vue";
</script>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
