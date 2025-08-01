<template>
  <v-main class="dashboard-background">
    <v-dialog v-model="showDataSelection" persistent max-width="600" width="95%">
      <v-card>
        <v-card-title class="d-flex align-center">
          <v-icon class="mr-3" color="primary">mdi-database</v-icon>
          Seleccionar Fuente de Datos
        </v-card-title>
        <v-card-text class="pt-4">
          <p class="text-body-1 mb-4">
            ¿Qué datos desea utilizar para los dashboards?
          </p>
          <v-row>
            <v-col cols="12" md="6">
              <v-card 
                class="data-option-card" 
                :class="{ 'selected': selectedDataOption === 'default' }"
                @click="selectDataOption('default')"
                elevation="2"
              >
                <v-card-text class="text-center">
                  <v-icon size="48" color="primary" class="mb-3">mdi-file-document</v-icon>
                  <h3 class="text-h6 font-weight-bold mb-2">Datos por Defecto</h3>
                  <p class="text-body-2 text-grey">
                    Utilizar el archivo JSON incluido en el proyecto
                  </p>
                </v-card-text>
              </v-card>
            </v-col>
            <v-col cols="12" md="6">
              <v-card 
                class="data-option-card" 
                :class="{ 'selected': selectedDataOption === 'upload' }"
                @click="selectDataOption('upload')"
                elevation="2"
              >
                <v-card-text class="text-center">
                  <v-icon size="48" color="success" class="mb-3">mdi-upload</v-icon>
                  <h3 class="text-h6 font-weight-bold mb-2">Subir Archivo JSON</h3>
                  <p class="text-body-2 text-grey">
                    Cargar un archivo JSON personalizado
                  </p>
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>
          
          <div v-if="selectedDataOption === 'upload'" class="mt-4">
            <v-file-input
              v-model="uploadedFile"
              label="Seleccionar archivo JSON"
              accept=".json"
              prepend-icon="mdi-file-json"
              variant="outlined"
              color="primary"
              :rules="[fileRules]"
              @update:model-value="handleFileUpload"
            />
            <p class="text-caption text-grey mt-2">
              El archivo debe tener el mismo formato que el JSON por defecto
            </p>
          </div>
        </v-card-text>
        <v-card-actions class="pa-4">
          <v-spacer />
          <v-btn 
            color="primary" 
            @click="confirmDataSelection"
            :disabled="!canContinue"
          >
            Continuar
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>

    <v-card class="header-card" elevation="8">
      <v-card-title class="text-h3 text-center py-6">
        <v-icon size="48" class="mr-4" color="primary">mdi-chart-line</v-icon>
        Dashboard de Proyectos Ambientales
      </v-card-title>
      <v-card-subtitle class="text-h6 text-center pb-4">
        Análisis integral de proyectos ambientales en Chile
      </v-card-subtitle>
    </v-card>

    <v-container fluid class="dashboard-container pa-4">
      <v-row>
        <v-col cols="12">

          <v-row>
            <v-col cols="12">
              <v-card class="mb-6 filter-card" elevation="4">
                <v-card-title class="d-flex align-center">
                  <v-icon class="mr-3" color="primary">mdi-view-dashboard</v-icon>
                  Seleccionar Dashboard
                </v-card-title>
                <v-card-text class="pt-4">
                  <v-row>
                    <v-col cols="12" md="4">
                      <v-select
                        v-model="selectedDashboard"
                        :items="dashboardOptions"
                        label="Dashboard a Mostrar"
                        prepend-icon="mdi-chart-line"
                        variant="outlined"
                        color="primary"
                        @update:model-value="changeDashboard"
                      />
                    </v-col>
                    <v-col cols="12" md="4">
                      <v-select
                        v-model="selectedRegion"
                        :items="regions"
                        label="Filtrar por Región"
                        prepend-icon="mdi-map-marker"
                        clearable
                        variant="outlined"
                        color="primary"
                        @update:model-value="filterData"
                      />
                    </v-col>
                    <v-col cols="12" md="4">
                      <v-select
                        v-model="selectedYear"
                        :items="years"
                        label="Filtrar por Año"
                        prepend-icon="mdi-calendar"
                        clearable
                        variant="outlined"
                        color="primary"
                        @update:model-value="filterData"
                      />
                    </v-col>
                  </v-row>
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>

          <v-row v-if="selectedDashboard === 'all' || selectedDashboard === 'projects'">
            <v-col cols="12">
              <v-card class="mb-6 chart-card" elevation="6">
                <v-card-title class="d-flex align-center">
                  <v-icon class="mr-3" color="info">mdi-chart-bar</v-icon>
                  Proyectos Ingresados vs Aprobados por Año
                </v-card-title>
                <v-card-subtitle class="text-body-2">
                  Análisis de la evolución temporal de proyectos ambientales, mostrando la cantidad de proyectos ingresados y aprobados por año
                </v-card-subtitle>
                <v-card-text class="pt-4">
                  <ProjectsChart :chart-data="projectsChartData" />
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>

          <v-row v-if="selectedDashboard === 'all' || selectedDashboard === 'investment'">
            <v-col cols="12">
              <v-card class="mb-6 chart-card" elevation="6">
                <v-card-title class="d-flex align-center">
                  <v-icon class="mr-3" color="success">mdi-currency-usd</v-icon>
                  Inversión por Año y Tipo de Proyecto
                </v-card-title>
                <v-card-subtitle class="text-body-2">
                  Análisis de inversiones agrupadas por año y tipo de proyecto (DIA/EIA), mostrando la distribución de recursos financieros
                </v-card-subtitle>
                <v-card-text class="pt-4">
                  <InvestmentChart :chart-data="investmentChartData" />
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>

          <v-row v-if="selectedDashboard === 'all' || selectedDashboard === 'processing'">
            <v-col cols="12">
              <v-card class="mb-6 chart-card" elevation="6">
                <v-card-title class="d-flex align-center">
                  <v-icon class="mr-3" color="warning">mdi-clock-outline</v-icon>
                  Tiempo de Tramitación por Año y Tipo
                </v-card-title>
                <v-card-subtitle class="text-body-2">
                  Análisis de eficiencia en tiempos de tramitación, calculando la diferencia entre fecha de ingreso y fecha de resolución
                </v-card-subtitle>
                <v-card-text class="pt-4">
                  <ProcessingTimeChart :chart-data="processingTimeChartData" />
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>

          <v-row>
            <v-col cols="12" md="3">
              <v-card class="stat-card" elevation="4">
                <v-card-text class="text-center">
                  <v-icon size="48" color="primary" class="mb-2">mdi-file-document</v-icon>
                  <div class="text-h4 font-weight-bold text-primary">{{ totalProjects }}</div>
                  <div class="text-subtitle-1">Total Proyectos</div>
                </v-card-text>
              </v-card>
            </v-col>
            <v-col cols="12" md="3">
              <v-card class="stat-card" elevation="4">
                <v-card-text class="text-center">
                  <v-icon size="48" color="success" class="mb-2">mdi-check-circle</v-icon>
                  <div class="text-h4 font-weight-bold text-success">{{ approvedProjects }}</div>
                  <div class="text-subtitle-1">Proyectos Aprobados</div>
                </v-card-text>
              </v-card>
            </v-col>
            <v-col cols="12" md="3">
              <v-card class="stat-card" elevation="4">
                <v-card-text class="text-center">
                  <v-icon size="48" color="info" class="mb-2">mdi-map</v-icon>
                  <div class="text-h4 font-weight-bold text-info">{{ uniqueRegions }}</div>
                  <div class="text-subtitle-1">Regiones</div>
                </v-card-text>
              </v-card>
            </v-col>
            <v-col cols="12" md="3">
              <v-card class="stat-card" elevation="4">
                <v-card-text class="text-center">
                  <v-icon size="48" color="warning" class="mb-2">mdi-calendar-range</v-icon>
                  <div class="text-h4 font-weight-bold text-warning">{{ averageProcessingTime }}</div>
                  <div class="text-subtitle-1">Días Promedio</div>
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </v-container>
  </v-main>
</template>

<script setup lang="ts">
import { ref, computed, onMounted } from 'vue'
import ProjectsChart from './charts/ProjectsChart.vue'
import InvestmentChart from './charts/InvestmentChart.vue'
import ProcessingTimeChart from './charts/ProcessingTimeChart.vue'

interface Project {
  id: string
  nombre: string
  fecha: string
  fecha_resolucion: string | null
  estado: string
  tipo: string
  region: string
  inversion: string
}

const projects = ref<Project[]>([])
const selectedRegion = ref<string>('')
const selectedYear = ref<string>('')
const selectedDashboard = ref<string>('all')

const showDataSelection = ref<boolean>(true)
const selectedDataOption = ref<string>('')
const uploadedFile = ref<File | null>(null)

const dashboardOptions = [
  { title: 'Todos los Dashboards', value: 'all' },
  { title: 'Proyectos Ingresados vs Aprobados', value: 'projects' },
  { title: 'Inversión por Año y Tipo', value: 'investment' },
  { title: 'Tiempo de Tramitación', value: 'processing' }
]

const filteredProjects = computed(() => {
  let filtered = projects.value

  if (selectedRegion.value) {
    filtered = filtered.filter(project => project.region === selectedRegion.value)
  }

  if (selectedYear.value) {
    filtered = filtered.filter(project => {
      const fechaParts = project.fecha.split('-')
      const projectYear = fechaParts.length === 3 ? fechaParts[2] : new Date(project.fecha).getFullYear().toString()
      return projectYear === selectedYear.value
    })
  }

  return filtered
})

const regions = computed(() => {
  const uniqueRegions = [...new Set(projects.value.map(p => p.region))]
  return uniqueRegions.sort()
})

const years = computed(() => {
  const uniqueYears = [...new Set(projects.value.map(p => {
    const fechaParts = p.fecha.split('-')
    return fechaParts.length === 3 ? fechaParts[2] : new Date(p.fecha).getFullYear().toString()
  }))]
  return uniqueYears.sort()
})

const totalProjects = computed(() => filteredProjects.value.length)

const approvedProjects = computed(() => 
  filteredProjects.value.filter(project => project.estado === 'Aprobado').length
)

const uniqueRegions = computed(() => regions.value.length)

const averageProcessingTime = computed(() => {
  const projectsWithResolution = filteredProjects.value.filter(p => p.fecha_resolucion)
  if (projectsWithResolution.length === 0) return 0
  
  const totalDays = projectsWithResolution.reduce((total, project) => {
    const fechaInicio = new Date(project.fecha.split('-').reverse().join('-'))
    const fechaResolucion = new Date(project.fecha_resolucion!.split('-').reverse().join('-'))
    const diasDiferencia = Math.ceil((fechaResolucion.getTime() - fechaInicio.getTime()) / (1000 * 60 * 60 * 24))
    return total + diasDiferencia
  }, 0)
  
  return Math.round(totalDays / projectsWithResolution.length)
})

const projectsChartData = computed(() => {
  const dataByYear: { [key: string]: { ingresados: number; aprobados: number } } = {}

  filteredProjects.value.forEach(project => {
    const fechaParts = project.fecha.split('-')
    const year = fechaParts.length === 3 ? fechaParts[2] : new Date(project.fecha).getFullYear().toString()

    if (!dataByYear[year]) {
      dataByYear[year] = { ingresados: 0, aprobados: 0 }
    }

    dataByYear[year].ingresados++

    if (project.estado === 'Aprobado') {
      dataByYear[year].aprobados++
    }
  })

  const years = Object.keys(dataByYear).sort()

  return {
    labels: years,
    datasets: [
      {
        label: 'Proyectos Ingresados',
        data: years.map(year => dataByYear[year].ingresados),
        backgroundColor: 'rgba(54, 162, 235, 0.7)',
        borderColor: 'rgba(54, 162, 235, 1)',
        borderWidth: 2
      },
      {
        label: 'Proyectos Aprobados',
        data: years.map(year => dataByYear[year].aprobados),
        backgroundColor: 'rgba(75, 192, 192, 0.7)',
        borderColor: 'rgba(75, 192, 192, 1)',
        borderWidth: 2
      }
    ]
  }
})

const investmentChartData = computed(() => {
  const dataByYearAndType: { [key: string]: { [key: string]: number } } = {}

  filteredProjects.value.forEach(project => {
    const fechaParts = project.fecha.split('-')
    const year = fechaParts.length === 3 ? fechaParts[2] : new Date(project.fecha).getFullYear().toString()
    const tipo = project.tipo
    
    const inversion = parseFloat(project.inversion.replace(/[^\d.-]/g, '')) || 0

    if (!dataByYearAndType[year]) {
      dataByYearAndType[year] = {}
    }
    
    if (!dataByYearAndType[year][tipo]) {
      dataByYearAndType[year][tipo] = 0
    }
    
    dataByYearAndType[year][tipo] += inversion
  })

  const years = Object.keys(dataByYearAndType).sort()
  const tipos = ['DIA', 'EIA']
  
  return {
    labels: years,
    datasets: tipos.map(tipo => ({
      label: tipo,
      data: years.map(year => dataByYearAndType[year][tipo] || 0),
      backgroundColor: tipo === 'DIA' ? 'rgba(255, 99, 132, 0.7)' : 'rgba(255, 205, 86, 0.7)',
      borderColor: tipo === 'DIA' ? 'rgba(255, 99, 132, 1)' : 'rgba(255, 205, 86, 1)',
      borderWidth: 2
    }))
  }
})

const processingTimeChartData = computed(() => {
  const dataByYearAndType: { [key: string]: { [key: string]: number[] } } = {}

  filteredProjects.value.forEach(project => {
    if (!project.fecha_resolucion) return

    const fechaParts = project.fecha.split('-')
    const year = fechaParts.length === 3 ? fechaParts[2] : new Date(project.fecha).getFullYear().toString()
    const tipo = project.tipo
    
    const fechaInicio = new Date(project.fecha.split('-').reverse().join('-'))
    const fechaResolucion = new Date(project.fecha_resolucion.split('-').reverse().join('-'))
    const diasDiferencia = Math.ceil((fechaResolucion.getTime() - fechaInicio.getTime()) / (1000 * 60 * 60 * 24))

    if (!dataByYearAndType[year]) {
      dataByYearAndType[year] = {}
    }
    
    if (!dataByYearAndType[year][tipo]) {
      dataByYearAndType[year][tipo] = []
    }
    
    dataByYearAndType[year][tipo].push(diasDiferencia)
  })

  const years = Object.keys(dataByYearAndType).sort()
  const tipos = ['DIA', 'EIA']
  
  return {
    labels: years,
    datasets: tipos.map(tipo => ({
      label: `Promedio ${tipo}`,
      data: years.map(year => {
        const tiempos = dataByYearAndType[year]?.[tipo] || []
        return tiempos.length > 0 ? tiempos.reduce((a, b) => a + b, 0) / tiempos.length : 0
      }),
      backgroundColor: tipo === 'DIA' ? 'rgba(153, 102, 255, 0.7)' : 'rgba(255, 159, 64, 0.7)',
      borderColor: tipo === 'DIA' ? 'rgba(153, 102, 255, 1)' : 'rgba(255, 159, 64, 1)',
      borderWidth: 2
    }))
  }
})

const canContinue = computed(() => {
  if (!selectedDataOption.value) return false
  if (selectedDataOption.value === 'default') return true
  if (selectedDataOption.value === 'upload') return uploadedFile.value !== null
  return false
})

const fileRules = (value: File | null) => {
  if (!value) return 'Debe seleccionar un archivo'
  if (value.type !== 'application/json') return 'El archivo debe ser JSON'
  return true
}

const filterData = () => {
}

const changeDashboard = () => {
}

const selectDataOption = (option: string) => {
  selectedDataOption.value = option
  if (option === 'default') {
    uploadedFile.value = null
  }
}

const handleFileUpload = (files: File | File[]) => {
  if (Array.isArray(files)) {
    uploadedFile.value = files[0] || null
  } else {
    uploadedFile.value = files
  }
}

const confirmDataSelection = async () => {
  if (selectedDataOption.value === 'default') {
    await loadDefaultData()
  } else if (selectedDataOption.value === 'upload' && uploadedFile.value) {
    await loadUploadedData()
  }
  
  showDataSelection.value = false
}

const loadDefaultData = async () => {
  try {
    const response = await fetch('/data/proyectos.json')
    projects.value = await response.json()
  } catch (error) {
    console.error('Error cargando datos por defecto:', error)
    projects.value = []
  }
}

const loadUploadedData = async () => {
  if (!uploadedFile.value) return
  
  try {
    const text = await uploadedFile.value.text()
    const data = JSON.parse(text)
    
    if (Array.isArray(data) && data.length > 0 && data[0].id) {
      projects.value = data
    } else {
      throw new Error('Formato de archivo inválido')
    }
  } catch (error) {
    console.error('Error cargando archivo subido:', error)
    alert('Error al cargar el archivo. Asegúrese de que tenga el formato correcto.')
    projects.value = []
  }
}

const loadData = async () => {
  try {
    const response = await fetch('/data/proyectos.json')
    projects.value = await response.json()
  } catch (error) {
    console.error('Error cargando datos:', error)
    projects.value = []
  }
}

onMounted(() => {
})
</script>

<style scoped>
.dashboard-background {
  background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
  min-height: 100vh;
  width: 100%;
}

.dashboard-container {
  max-width: 100% !important;
  width: 100% !important;
}

.header-card {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  border-radius: 0;
  width: 100%;
  margin: 0;
  box-shadow: none;
}

.header-card .v-card-title {
  color: white !important;
  font-weight: 700;
}

.header-card .v-card-subtitle {
  color: rgba(255, 255, 255, 0.9) !important;
}

.filter-card {
  background: white;
  border-radius: 0;
  border-left: 4px solid #1976d2;
  width: 100%;
}

.chart-card {
  background: white;
  border-radius: 0;
  transition: transform 0.2s ease-in-out;
  width: 100%;
}

.chart-card:hover {
  transform: translateY(-2px);
}

.stat-card {
  background: white;
  border-radius: 0;
  transition: transform 0.2s ease-in-out;
  cursor: pointer;
  width: 100%;
}

.stat-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15) !important;
}

.v-card {
  border-radius: 0;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
  overflow: hidden;
  width: 100%;
}

.v-card-title {
  color: #1976d2;
  font-weight: 600;
  padding: 24px 24px 16px 24px;
}

.v-card-text {
  padding: 0 24px 24px 24px;
}

.v-select {
  margin-bottom: 8px;
}

.text-body-2 {
  word-wrap: break-word !important;
  white-space: normal !important;
  overflow-wrap: break-word !important;
}

@media (max-width: 768px) {
  .dashboard-container {
    padding: 16px !important;
  }
  
  .v-card-title {
    font-size: 1.5rem !important;
  }
  
  .stat-card .v-card-text {
    padding: 16px !important;
  }
  
  .header-card .v-card-title {
    font-size: 1.75rem !important;
  }
  
  .header-card .v-card-subtitle {
    font-size: 1rem !important;
  }
  
  .v-icon {
    font-size: 24px !important;
  }
  
  .data-option-card .v-icon {
    font-size: 36px !important;
  }
}

@media (max-width: 480px) {
  .dashboard-container {
    padding: 8px !important;
  }
  
  .v-card-title {
    font-size: 1.25rem !important;
    padding: 16px 16px 12px 16px !important;
  }
  
  .v-card-text {
    padding: 0 16px 16px 16px !important;
  }
  
  .header-card .v-card-title {
    font-size: 1.5rem !important;
    padding: 16px !important;
  }
  
  .header-card .v-card-subtitle {
    font-size: 0.875rem !important;
    padding: 0 16px 16px 16px !important;
  }
  
  .stat-card .v-card-text {
    padding: 12px !important;
  }
  
  .stat-card .text-h4 {
    font-size: 1.5rem !important;
  }
  
  .stat-card .text-subtitle-1 {
    font-size: 0.75rem !important;
  }
}

.v-main {
  width: 100% !important;
  max-width: 100% !important;
}

.v-container {
  max-width: 100% !important;
  width: 100% !important;
}

.data-option-card {
  cursor: pointer;
  transition: all 0.3s ease;
  border: 2px solid transparent;
}

.data-option-card:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
}

.data-option-card.selected {
  border-color: #1976d2;
  background-color: rgba(25, 118, 210, 0.05);
}

.data-option-card.selected .v-icon {
  color: #1976d2 !important;
}

@media (max-width: 768px) {
  .data-option-card .v-card-text {
    padding: 16px !important;
  }
  
  .data-option-card .text-h6 {
    font-size: 1rem !important;
  }
  
  .data-option-card .text-body-2 {
    font-size: 0.875rem !important;
  }
  
  .chart-card .v-card-title {
    font-size: 1.25rem !important;
    line-height: 1.3 !important;
    word-wrap: break-word !important;
    white-space: normal !important;
  }
  
  .chart-card .v-card-subtitle {
    font-size: 0.875rem !important;
    line-height: 1.4 !important;
    word-wrap: break-word !important;
    white-space: normal !important;
    overflow-wrap: break-word !important;
  }
  
  .text-body-2 {
    font-size: 0.875rem !important;
    line-height: 1.4 !important;
  }
}

@media (max-width: 480px) {
  .data-option-card .v-card-text {
    padding: 12px !important;
  }
  
  .data-option-card .text-h6 {
    font-size: 0.875rem !important;
  }
  
  .data-option-card .text-body-2 {
    font-size: 0.75rem !important;
  }
  
  .data-option-card .v-icon {
    font-size: 32px !important;
  }
  
  .chart-card .v-card-title {
    font-size: 1rem !important;
    line-height: 1.2 !important;
    word-wrap: break-word !important;
    white-space: normal !important;
    padding: 12px 12px 8px 12px !important;
  }
  
  .chart-card .v-card-subtitle {
    font-size: 0.75rem !important;
    line-height: 1.3 !important;
    padding: 0 12px 8px 12px !important;
    word-wrap: break-word !important;
    white-space: normal !important;
    overflow-wrap: break-word !important;
    hyphens: auto !important;
  }
  
  .text-body-2 {
    font-size: 0.75rem !important;
    line-height: 1.3 !important;
  }
}

@media (max-width: 360px) {
  .chart-card .v-card-title {
    font-size: 0.875rem !important;
    padding: 10px 10px 6px 10px !important;
  }
  
  .chart-card .v-card-subtitle {
    font-size: 0.7rem !important;
    padding: 0 10px 6px 10px !important;
    word-wrap: break-word !important;
    white-space: normal !important;
    overflow-wrap: break-word !important;
    hyphens: auto !important;
    line-height: 1.2 !important;
  }
  
  .text-body-2 {
    font-size: 0.7rem !important;
    line-height: 1.2 !important;
  }
}
</style> 