<template>
    <div class="space-y-6">
      <h1 class="text-3xl font-bold mb-4">🚫 AutoMod Ayarları</h1>
  
      <div>
        <label class="block text-sm font-medium mb-1">Sunucu Seç</label>
        <select v-model="selectedGuild" class="w-full p-2 rounded bg-gray-800 border border-gray-700 focus:outline-none mb-4">
          <option v-for="guild in guilds" :key="guild.id" :value="guild.id">
            {{ guild.name }}
          </option>
        </select>
      </div>
  
      <div class="grid md:grid-cols-2 gap-6">
        <div class="bg-gray-800 p-4 rounded shadow">
          <label class="flex items-center gap-2">
            <input type="checkbox" v-model="settings.capsLock" class="accent-emerald-500" />
            Büyük Harf Engelleme
          </label>
        </div>
  
        <div class="bg-gray-800 p-4 rounded shadow">
          <label class="flex items-center gap-2">
            <input type="checkbox" v-model="settings.inviteLinks" class="accent-emerald-500" />
            Davet Linki Engelleme
          </label>
        </div>
  
        <div class="bg-gray-800 p-4 rounded shadow">
          <label class="flex items-center gap-2">
            <input type="checkbox" v-model="settings.spamDetection" class="accent-emerald-500" />
            Spam Mesaj Algılama
          </label>
        </div>
  
        <div class="bg-gray-800 p-4 rounded shadow">
          <label class="flex items-center gap-2">
            <input type="checkbox" v-model="settings.badWords" class="accent-emerald-500" />
            Küfür Filtresi
          </label>
        </div>
      </div>
  
      <button class="bg-emerald-500 hover:bg-emerald-600 text-white px-6 py-2 rounded shadow mt-4" @click="saveSettings">
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
  
  const settings = ref({
    capsLock: true,
    inviteLinks: false,
    spamDetection: true,
    badWords: false
  })
  
  watch(selectedGuild, (id) => {
    // TODO: API'den otomod ayarlarını çek
    console.log('Sunucu değişti, AutoMod ayarları çekiliyor:', id)
    settings.value = id === '123' ? {
      capsLock: true,
      inviteLinks: false,
      spamDetection: true,
      badWords: false
    } : {
      capsLock: false,
      inviteLinks: true,
      spamDetection: false,
      badWords: true
    }
  })
  
  function saveSettings() {
    // TODO: API'ye ayarları gönder
    console.log('AutoMod ayarları kaydedildi:', selectedGuild.value, settings.value)
  }
  </script>
  