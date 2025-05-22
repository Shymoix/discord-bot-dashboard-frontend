<template>
    <div class="space-y-6">
      <h1 class="text-3xl font-bold mb-4">🎮 Eğlence Komutları</h1>
  
      <div>
        <label class="block text-sm font-medium mb-1">Sunucu Seç</label>
        <select v-model="selectedGuild" class="w-full p-2 rounded bg-gray-800 border border-gray-700 focus:outline-none mb-4">
          <option v-for="guild in guilds" :key="guild.id" :value="guild.id">
            {{ guild.name }}
          </option>
        </select>
      </div>
  
      <div class="grid md:grid-cols-2 gap-6">
        <div v-for="command in funCommands" :key="command.name" class="bg-gray-800 p-4 rounded shadow">
          <div class="flex items-center justify-between">
            <span class="font-medium">{{ command.label }}</span>
            <input type="checkbox" v-model="command.enabled" class="accent-emerald-500" />
          </div>
          <p class="text-sm text-gray-400 mt-1">{{ command.description }}</p>
        </div>
      </div>
  
      <button class="bg-emerald-500 hover:bg-emerald-600 text-white px-6 py-2 rounded shadow mt-4" @click="saveFunSettings">
        Ayarları Kaydet
      </button>
    </div>
  </template>
  
  <script setup>
  import { ref, watch } from 'vue'
  
  const selectedGuild = ref('123')
  const guilds = [
    { id: '123', name: 'WatchAni Sunucusu' },
    { id: '456', name: 'AnimeClub' }
  ]
  
  const funCommands = ref([
    {
      name: 'fal',
      label: 'Kahve Falı',
      description: 'Kullanıcılara rastgele kahve falı gönderir.',
      enabled: true
    },
    {
      name: 'iltifat',
      label: 'İltifat',
      description: 'Kullanıcılara rastgele iltifat eder.',
      enabled: true
    },
    {
      name: 'diss',
      label: 'Diss',
      description: 'Rastgele diss cümlesi atar.',
      enabled: true
    },
    {
      name: 'tictactoe',
      label: 'TicTacToe',
      description: '2 kişilik eğlenceli kutu oyunu.',
      enabled: false
    },
    {
      name: 'akinator',
      label: 'Akinator',
      description: 'Aklındaki karakteri tahmin etmeye çalışır.',
      enabled: false
    }
  ])
  
  watch(selectedGuild, (id) => {
    // TODO: API'den komut ayarlarını çek
    console.log('Sunucu değişti, eğlence ayarları çekiliyor:', id)
  })
  
  function saveFunSettings() {
    // TODO: API'ye komut ayarlarını gönder
    console.log('Eğlence ayarları kaydedildi:', selectedGuild.value, funCommands.value)
  }
  </script>
  