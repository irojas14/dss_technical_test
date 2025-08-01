<template>
  <div class="chart-container">
    <Line
      :data="chartData"
      :options="chartOptions"
      class="chart"
    />
  </div>
</template>

<script setup lang="ts">
import { Line } from 'vue-chartjs'
import {
  Chart as ChartJS,
  CategoryScale,
  LinearScale,
  PointElement,
  LineElement,
  Title,
  Tooltip,
  Legend
} from 'chart.js'

ChartJS.register(
  CategoryScale,
  LinearScale,
  PointElement,
  LineElement,
  Title,
  Tooltip,
  Legend
)

interface Props {
  chartData: {
    labels: string[]
    datasets: Array<{
      label: string
      data: number[]
      backgroundColor: string
      borderColor: string
      borderWidth: number
    }>
  }
}

const props = defineProps<Props>()

const chartOptions = {
  responsive: true,
  maintainAspectRatio: false,
  plugins: {
    legend: {
      position: 'top' as const,
      labels: {
        boxWidth: 12,
        padding: 15,
        font: {
          size: window.innerWidth < 768 ? 10 : 12
        }
      }
    },
    title: {
      display: true,
      text: window.innerWidth < 480 ? 'Tiempo de Tramitación por Año' : 
            window.innerWidth < 768 ? 'Tiempo Promedio de Tramitación por Año' : 
            'Tiempo Promedio de Tramitación por Año y Tipo (Diferencia de Fechas)',
      font: {
        size: window.innerWidth < 480 ? 12 : window.innerWidth < 768 ? 14 : 16
      },
      padding: {
        top: window.innerWidth < 480 ? 8 : 16,
        bottom: window.innerWidth < 480 ? 8 : 16
      }
    },
    tooltip: {
      callbacks: {
        label: function(context: any) {
          const value = context.parsed.y
          return `${context.dataset.label}: ${Math.round(value)} días`
        }
      }
    }
  },
  scales: {
    y: {
      beginAtZero: true,
      title: {
        display: true,
        text: window.innerWidth < 480 ? 'Días de Tramitación' : 'Días Promedio de Tramitación',
        font: {
          size: window.innerWidth < 480 ? 9 : window.innerWidth < 768 ? 10 : 12
        }
      },
      ticks: {
        callback: function(value: any) {
          return Math.round(value) + ' días'
        },
        font: {
          size: window.innerWidth < 480 ? 9 : window.innerWidth < 768 ? 10 : 12
        }
      }
    },
    x: {
      title: {
        display: true,
        text: 'Año',
        font: {
          size: window.innerWidth < 480 ? 9 : window.innerWidth < 768 ? 10 : 12
        }
      },
      ticks: {
        font: {
          size: window.innerWidth < 480 ? 9 : window.innerWidth < 768 ? 10 : 12
        }
      }
    }
  }
}
</script>

<style scoped>
.chart-container {
  position: relative;
  height: 400px;
  width: 100%;
}

.chart {
  height: 100% !important;
}

@media (max-width: 768px) {
  .chart-container {
    height: 300px;
  }
}

@media (max-width: 480px) {
  .chart-container {
    height: 250px;
  }
}
</style> 