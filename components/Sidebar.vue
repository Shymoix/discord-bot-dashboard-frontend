<template>
    <aside class="w-64 bg-gray-800 p-4 space-y-4">
      <h1 class="text-2xl font-bold mb-4">Kaave</h1>
      <nav class="flex flex-col gap-2">
        <NuxtLink to="/" class="hover:bg-gray-700 rounded p-2">🏠 Dashboard</NuxtLink>
        <NuxtLink to="/guild" class="hover:bg-gray-700 rounded p-2">⚙️ Sunucu Ayarları</NuxtLink>
        <NuxtLink to="/moderation" class="hover:bg-gray-700 rounded p-2">📜 Moderasyon</NuxtLink>
        <NuxtLink to="/automod" class="hover:bg-gray-700 rounded p-2">🚫 AutoMod</NuxtLink>
        <NuxtLink to="/fun" class="hover:bg-gray-700 rounded p-2">🎮 Eğlence</NuxtLink>
        <NuxtLink to="/stats" class="hover:bg-gray-700 rounded p-2">📊 İstatistik</NuxtLink>
        <NuxtLink to="/admin" class="hover:bg-gray-700 rounded p-2">👑 Admin Panel</NuxtLink>
      </nav>
    </aside>
  </template>