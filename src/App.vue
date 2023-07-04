<script setup lang="ts">
import { onMounted, ref } from 'vue';
const theme = ref('System');

const toggleTheme = async () => {
  // @ts-ignore
  const isDarkMode = await window.darkMode.toggle();
  theme.value = isDarkMode ? 'Dark' : 'Light';
};

const resetSystem = async () => {
  // @ts-ignore
  await window.darkMode.system();
  theme.value = 'System';
};

onMounted(() => {
  window.postMessage('removeLoading', '*');
});
console.log(`Hello world from Electron!`);
</script>

<template>
  <p>
    Current theme source: <strong id="theme-source">{{ theme }}</strong>
  </p>
  <button @click="toggleTheme">Toggle Dark</button><br />
  <button @click="resetSystem">Reset to System Theme</button>
</template>
