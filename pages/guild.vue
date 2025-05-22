<template>
    <div class="space-y-6">
      <h1 class="text-3xl font-bold mb-4">⚙️ Sunucu Ayarları</h1>
  
      <div>
        <label class="block text-sm font-medium mb-1">Sunucu Seç</label>
        <select v-model="selectedGuild" class="w-full p-2 rounded bg-gray-800 border border-gray-700 focus:outline-none mb-4">
          <option v-for="guild in guilds" :key="guild.id" :value="guild.id">
            {{ guild.name }}
          </option>
        </select>
      </div>
  
      <div class="grid md:grid-cols-2 gap-6">
        <div>
          <label class="block text-sm font-medium mb-1">Prefix</label>
          <input v-model="prefix" type="text" class="w-full p-2 rounded bg-gray-800 border border-gray-700 focus:outline-none" />
        </div>
  
        <div>
          <label class="block text-sm font-medium mb-1">Log Kanalı</label>
          <select v-model="logChannel" class="w-full p-2 rounded bg-gray-800 border border-gray-700 focus:outline-none">
            <option v-for="channel in channels" :key="channel.id" :value="channel.id">
              #{{ channel.name }}
            </option>
          </select>
        </div>
  
        <div>
          <label class="block text-sm font-medium mb-1">Otorol</label>
          <select v-model="autoRole" class="w-full p-2 rounded bg-gray-800 border border-gray-700 focus:outline-none">
            <option value="">Kapalı</option>
            <option v-for="role in roles" :key="role.id" :value="role.id">
              {{ role.name }}
            </option>
          </select>
        </div>
  
        <div>
          <label class="block text-sm font-medium mb-1">Komut Aktifliği</label>
          <div class="flex gap-2 flex-wrap">
            <div v-for="cmd in commands" :key="cmd.name" class="bg-gray-800 px-4 py-2 rounded shadow text-sm">
              <input type="checkbox" v-model="cmd.enabled" class="mr-2" /> {{ cmd.name }}
            </div>
          </div>
        </div>
      </div>
  
      <button class="bg-emerald-500 hover:bg-emerald-600 text-white px-6 py-2 rounded shadow mt-4" @click="saveSettings">
        Kaydet
      </button>
    </div>
  </template>
  
  <script setup>
  import { ref, watch } from 'vue'
  
  const selectedGuild = ref('')
  const prefix = ref('!')
  const logChannel = ref('')
  const autoRole = ref('')
  
  const guilds = [
    { id: '123', name: 'WatchAni Sunucusu' },
    { id: '456', name: 'AnimeClub' }
  ]
  
  const channels = [
    { id: '1', name: 'genel' },
    { id: '2', name: 'log-kanalı' },
  ]
  
  const roles = [
    { id: 'a', name: 'Üye' },
    { id: 'b', name: 'Kayıtsız' },
  ]
  
  const commands = ref([
    { name: 'ban', enabled: true },
    { name: 'kick', enabled: true },
    { name: 'mute', enabled: false },
  ])
  
  watch(selectedGuild, (guildId) => {
    // TODO: API'den guildId'ye özel ayarları çek
    console.log('Sunucu değişti:', guildId)
    // Dummy response simülasyonu
    prefix.value = '!'
    logChannel.value = '2'
    autoRole.value = 'a'
    commands.value = [
      { name: 'ban', enabled: true },
      { name: 'kick', enabled: false },
      { name: 'mute', enabled: true },
    ]
  })
  
  function saveSettings() {
    console.log('Ayarlar kaydedildi', {
      guildId: selectedGuild.value,
      prefix: prefix.value,
      logChannel: logChannel.value,
      autoRole: autoRole.value,
      commands: commands.value,
    })
  }
  </script>