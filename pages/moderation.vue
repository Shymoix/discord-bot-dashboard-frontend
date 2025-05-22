<template>
    <div class="space-y-6">
      <h1 class="text-3xl font-bold mb-4">📜 Moderasyon Logları</h1>
  
      <table class="w-full text-left bg-gray-800 rounded-lg overflow-hidden">
        <thead class="bg-gray-700 text-sm uppercase text-gray-400">
          <tr>
            <th class="p-3">Kullanıcı</th>
            <th class="p-3">İşlem</th>
            <th class="p-3">Yetkili</th>
            <th class="p-3">Tarih</th>
            <th class="p-3">Sebep</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="log in logs" :key="log.id" class="border-b border-gray-700 hover:bg-gray-700">
            <td class="p-3 flex items-center gap-2">
              <img :src="log.user.avatar" class="w-8 h-8 rounded-full" />
              {{ log.user.name }}
            </td>
            <td class="p-3">{{ log.action }}</td>
            <td class="p-3">{{ log.moderator }}</td>
            <td class="p-3">{{ log.date }}</td>
            <td class="p-3 text-sm text-gray-300">{{ log.reason }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </template>
  
  <script setup>
  const logs = [
    {
      id: 1,
      user: { name: 'Neco', avatar: 'https://cdn.discordapp.com/embed/avatars/0.png' },
      action: 'Ban',
      moderator: 'Furkan',
      date: '2025-05-02',
      reason: 'Küfürlü konuşma'
    },
    {
      id: 2,
      user: { name: 'Mert', avatar: 'https://cdn.discordapp.com/embed/avatars/1.png' },
      action: 'Mute',
      moderator: 'Emir',
      date: '2025-05-01',
      reason: 'Spam mesajlar'
    },
    {
      id: 3,
      user: { name: 'Zeynep', avatar: 'https://cdn.discordapp.com/embed/avatars/2.png' },
      action: 'Kick',
      moderator: 'Kaave',
      date: '2025-04-30',
      reason: 'Trolllük'
    },
  ]
  </script>