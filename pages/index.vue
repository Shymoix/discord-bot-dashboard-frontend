<template>
    <div class="space-y-8">
      <div>
        <label class="block text-sm font-medium mb-1">Sunucu Seç</label>
        <select v-model="selectedGuild" class="w-full p-2 rounded bg-gray-800 border border-gray-700 focus:outline-none mb-4">
          <option v-for="guild in guilds" :key="guild.id" :value="guild.id">
            {{ guild.name }}
          </option>
        </select>
      </div>
  
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
        <StatCard title="Sunucu Üye Sayısı" :value="stats.memberCount" icon="👥" />
        <StatCard title="Aktif Komutlar" :value="stats.activeCommands" icon="🧩" />
        <StatCard title="Bugün Atılan Mesaj" :value="stats.todayMessages" icon="💬" />
        <StatCard title="Bugünkü Ban Sayısı" :value="stats.todayBans" icon="🔨" />
        <StatCard title="Uptime" :value="stats.uptime" icon="⚡" />
      </div>
  
      <MessageChart :guild-id="selectedGuild" />
    </div>
  </template>
  
  <script setup>
  import { ref, watch } from 'vue'
  import StatCard from '@/components/StatCard.vue'
  import MessageChart from '@/components/MessageChart.vue'
  
  const selectedGuild = ref('123')
  const guilds = [
    { id: '123', name: 'WatchAni Sunucusu' },
    { id: '456', name: 'AnimeClub' }
  ]
  
  const stats = ref({
    memberCount: '7420',
    activeCommands: '52',
    todayMessages: '13.000',
    todayBans: '4',
    uptime: '99.98%'
  })
  
  watch(selectedGuild, (id) => {
    // TODO: API'den sunucuya özel istatistik verisi çek
    console.log('Dashboard için sunucu değişti:', id)
    stats.value = id === '123' ? {
      memberCount: '7420',
      activeCommands: '52',
      todayMessages: '13.000',
      todayBans: '4',
      uptime: '99.98%'
    } : {
      memberCount: '342',
      activeCommands: '40',
      todayMessages: '740',
      todayBans: '1',
      uptime: '96.31%'
    }
  })
  </script>
  