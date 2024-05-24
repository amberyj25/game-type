<template>
  <main>
    <gameType />
  </main>
</template>

<script setup>
import gameType from './components/GameType.vue'
</script>


<style scoped>
main {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background: url('@/assets/game.jpg') no-repeat center center;
  background-size: cover;
}
</style>