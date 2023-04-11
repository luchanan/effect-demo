<script setup lang="ts">
import Manual from './components/Manual.vue'
</script>

<template>
  <el-tabs type="border-card">
    <el-tab-pane label="代码触发提交"><Manual /></el-tab-pane>
  </el-tabs>
</template>

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
