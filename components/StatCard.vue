<template>
    <div class="bg-gray-800 rounded-xl p-6 shadow hover:shadow-lg transition duration-300">
      <div class="text-3xl">{{ icon }}</div>
      <h2 class="text-xl font-semibold mt-2">{{ title }}</h2>
      <p class="text-4xl font-bold text-emerald-400">{{ value }}</p>
    </div>
  </template>
  
  <script setup>
  defineProps({
    title: String,
    value: String,
    icon: String
  })
  </script>