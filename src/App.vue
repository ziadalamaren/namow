<script setup>
import { ref, onMounted } from "vue";
import { SpeedInsights } from '@vercel/speed-insights/vue';

const dark = ref(false);

onMounted(() => {
  dark.value = localStorage.theme === "dark";
  if (dark.value) document.documentElement.classList.add("dark");
});

function toggleDark() {
  dark.value = !dark.value;
  document.documentElement.classList.toggle("dark");
  localStorage.theme = dark.value ? "dark" : "light";
}
</script>

<template>
  <router-view />
  <SpeedInsights />
</template>
