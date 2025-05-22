<template>
    <div class="flex h-screen bg-gray-900 text-white">
      <Sidebar />
      <div class="flex-1 flex flex-col">
        <Navbar />
        <div class="p-4 overflow-auto">
          <slot />
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  import Sidebar from '@/components/Sidebar.vue'
  import Navbar from '@/components/Navbar.vue'
  </script>