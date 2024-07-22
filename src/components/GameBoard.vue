<template>
  <div class="game-board">
    <template v-for="(row, rowIndex) in boardState">
      <GridCell
        v-for="(cell, cellIndex) in row"
        :key="`${rowIndex}-${cellIndex}`"
        :content="cell.content"
        :color="cellColors[cell.section]"
        :invalid="isValidQueen(rowIndex, cellIndex)"
        @click="handleToggleCell(rowIndex, cellIndex)"
      />
    </template>
  </div>
  <WinMessage v-if="gameWon" />
  <AppTimer />
  <AppButton @click="resetGame">Reset Game</AppButton>
  <AppButton @click="clearBoard">Clear Board</AppButton>
</template>

<script setup lang="ts">
import { onMounted } from "vue";
import GridCell from "@/components/GridCell.vue";
import { createGame } from "@/composables/createGame";
import WinMessage from "@/components/WinMessage.vue";
import AppTimer from "@/components/AppTimer.vue";
import { useTimer } from "@/composables/useTimer";
import AppButton from "@/components/AppButton.vue";
import { cellColors } from "@/data/cellColors.js";

const { boardState, gameWon, isValidQueen, toggleCell, clearBoard } =
  createGame();
const { startTimer, stopTimer, resetTimer } = useTimer();

function handleToggleCell(rowIndex: number, cellIndex: number) {
  toggleCell(rowIndex, cellIndex);

  if (gameWon.value) {
    stopTimer();
  }
}

function resetGame() {
  clearBoard();
  resetTimer();
}

onMounted(() => {
  startTimer();
});
</script>

<style scoped>
.game-board {
  display: grid;
  justify-content: center;
  grid-template-columns: repeat(8, 42px);
  grid-template-rows: repeat(8, 42px);
  border: 1px solid #000;
}
</style>
