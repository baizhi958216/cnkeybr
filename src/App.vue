<template>
  <div class="content">
    <text-bar />
    <!-- 键盘 -->
    <!-- <key-board /> -->
  </div>
</template>

<script setup lang="ts">
import TextBar from "./components/TextBar.vue";
// import KeyBoard from "./components/KeyBoard.vue";
</script>

<style scoped>
.content {
  /* width: 100vw; */
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  background-color: rgba(0, 0, 0, 0.151);
}
</style>
