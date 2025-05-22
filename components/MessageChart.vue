<template>
    <div class="bg-gray-800 p-6 rounded-xl shadow">
      <h2 class="text-xl font-semibold mb-4">📈 Haftalık Mesaj Aktivitesi</h2>
      <canvas ref="chartCanvas" height="100"></canvas>
    </div>
  </template>
  
  <script setup>
  import { onMounted, ref, watch } from 'vue'
  import { Chart, registerables } from 'chart.js'
  
  Chart.register(...registerables)
  
  const props = defineProps({
    guildId: String
  })
  
  const chartCanvas = ref(null)
  let chartInstance = null
  
  function renderChart(data) {
    if (chartInstance) {
      chartInstance.destroy()
    }
  
    chartInstance = new Chart(chartCanvas.value, {
      type: 'line',
      data: {
        labels: ['Pzt', 'Salı', 'Çar', 'Per', 'Cum', 'Cmt', 'Paz'],
        datasets: [
          {
            label: 'Mesaj Sayısı',
            data,
            fill: false,
            borderColor: 'rgb(34,197,94)',
            tension: 0.4
          }
        ]
      },
      options: {
        responsive: true,
        scales: {
          y: {
            beginAtZero: true
          }
        },
        plugins: {
          legend: {
            labels: {
              color: 'white'
            }
          }
        }
      }
    })
  }
  
  onMounted(() => {
    renderChart([1200, 980, 1350, 1600, 1100, 1450, 1700])
  })
  
  watch(() => props.guildId, (id) => {
    // TODO: API ile veriyi güncelle
    console.log('Grafik verisi değişti:', id)
    const dummy = id === '123'
      ? [1200, 980, 1350, 1600, 1100, 1450, 1700]
      : [300, 420, 250, 600, 350, 510, 720]
    renderChart(dummy)
  })
  </script>
  
  <style scoped>
  canvas {
    background-color: transparent;
  }
  </style>
  