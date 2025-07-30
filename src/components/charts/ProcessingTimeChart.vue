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
    },
    title: {
      display: true,
      text: 'Tiempo Promedio de Tramitación por Año y Tipo'
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
        text: 'Días Promedio'
      },
      ticks: {
        callback: function(value: any) {
          return Math.round(value) + ' días'
        }
      }
    },
    x: {
      title: {
        display: true,
        text: 'Año'
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
</style> 