// Admin Panel Sayfası - pages/admin.vue
<template>
  <div class="space-y-8">
    <h1 class="text-3xl font-bold">👑 Bot Admin Paneli</h1>

    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
      <StatCard title="Toplam Sunucu" :value="adminStats.totalGuilds" icon="🌐" />
      <StatCard title="Toplam Kullanıcı" :value="adminStats.totalUsers" icon="👥" />
      <StatCard title="Toplam Komut" :value="adminStats.totalCommands" icon="🧩" />
      <StatCard title="Bugünkü Toplam Mesaj" :value="adminStats.totalMessagesToday" icon="💬" />
      <StatCard title="Bugünkü Ban Sayısı" :value="adminStats.totalBansToday" icon="🔨" />
      <StatCard title="Bot Uptime" :value="adminStats.uptime" icon="⚡" />
    </div>

    <div class="grid md:grid-cols-3 gap-6">
      <div class="bg-gray-800 rounded-xl p-6 shadow space-y-3">
        <h2 class="text-xl font-semibold">🧪 Sürüm & Güncellemeler</h2>
        <p class="text-sm text-gray-300">🔁 Son Restart: {{ adminStats.lastRestart }}</p>
        <p class="text-sm text-gray-300">🧪 Bot Versiyonu: {{ adminStats.version }}</p>
        <p class="text-sm text-gray-300">❗ Son Hata Logu: <code class="text-red-400">{{ adminStats.lastError }}</code></p>
        <div class="flex gap-2 pt-2">
          <button class="bg-rose-500 hover:bg-rose-600 text-sm px-4 py-1 rounded">🔁 Restart Bot</button>
          <button class="bg-blue-500 hover:bg-blue-600 text-sm px-4 py-1 rounded">📥 Logları İndir</button>
        </div>
      </div>

      <div class="bg-gray-800 rounded-xl p-6 shadow space-y-3">
        <h2 class="text-xl font-semibold">📊 En Çok Kullanılan Komutlar</h2>
        <ul class="list-disc ml-5 text-sm text-gray-300 space-y-1">
          <li v-for="cmd in adminStats.topCommands" :key="cmd.name">
            {{ cmd.name }} - {{ cmd.count }} kez kullanıldı
          </li>
        </ul>
        <button class="mt-2 bg-yellow-500 hover:bg-yellow-600 text-sm px-4 py-1 rounded">📄 CSV olarak indir</button>
      </div>

      <div class="bg-gray-800 rounded-xl p-6 shadow space-y-3">
        <h2 class="text-xl font-semibold">🧠 Sistem Kaynak Kullanımı</h2>
        <p class="text-sm text-gray-300">💾 RAM Kullanımı: {{ adminStats.memoryUsage }}</p>
        <p class="text-sm text-gray-300">⚙️ CPU Kullanımı: {{ adminStats.cpuUsage }}</p>
        <button class="mt-2 bg-indigo-500 hover:bg-indigo-600 text-sm px-4 py-1 rounded">🔁 Yenile</button>
      </div>
    </div>

    <div class="bg-gray-800 rounded-xl p-6 shadow">
      <h2 class="text-xl font-semibold mb-4">🛡️ Yetkili Erişim</h2>
      <p class="text-sm text-gray-300">
        Bu sayfa sadece bot adminleri tarafından görüntülenebilir. Botun genel durumu ve sistemsel verileri burada listelenir.
      </p>
    </div>
  </div>
</template>

<script setup>
import StatCard from '@/components/StatCard.vue'

// NOT: Gerçek sistemde bu sayfa sadece isAdmin kullanıcılar tarafından erişilebilir olmalı
const adminStats = {
  totalGuilds: '2112',
  totalUsers: '88.734',
  totalCommands: '63',
  totalMessagesToday: '42.901',
  totalBansToday: '17',
  uptime: '99.982%',
  lastRestart: '2025-05-02 14:45',
  version: 'v1.6.4',
  lastError: 'TypeError: Cannot read properties of undefined',
  memoryUsage: '412 MB',
  cpuUsage: '7%',
  topCommands: [
    { name: 'fal', count: 12031 },
    { name: 'iltifat', count: 9821 },
    { name: 'avatar', count: 7634 },
    { name: 'ban', count: 5523 },
    { name: 'mute', count: 4432 },
  ]
}
</script>
