<template>
  <div class="chart-container">
    <Bar
      :data="chartData"
      :options="chartOptions"
      class="chart"
    />
  </div>
</template>

<script setup lang="ts">
import { Bar } from 'vue-chartjs'
import {
  Chart as ChartJS,
  CategoryScale,
  LinearScale,
  BarElement,
  Title,
  Tooltip,
  Legend
} from 'chart.js'

ChartJS.register(
  CategoryScale,
  LinearScale,
  BarElement,
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
      text: 'Inversión por Año y Tipo de Proyecto (Stacked Bar Chart)'
    },
    tooltip: {
      callbacks: {
        label: function(context: any) {
          const value = context.parsed.y
          return `${context.dataset.label}: $${value.toLocaleString('es-CL')}`
        }
      }
    }
  },
  scales: {
    y: {
      beginAtZero: true,
      stacked: true,
      title: {
        display: true,
        text: 'Inversión (USD)'
      },
      ticks: {
        callback: function(value: any) {
          return '$' + value.toLocaleString('es-CL')
        }
      }
    },
    x: {
      stacked: true,
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