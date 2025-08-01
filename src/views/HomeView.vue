<script setup lang="ts">
</script>

<template>
  <main class="home-background">
    <v-container fluid class="pa-0">
      <v-row>
        <v-col cols="12">
          <v-row class="hero-section" align="center" justify="center">
            <v-col cols="12" md="8" class="text-center">
              <div class="hero-content">
                <v-icon size="120" color="white" class="mb-6">mdi-leaf</v-icon>
                <h1 class="text-h2 font-weight-bold text-white mb-4">
                  Proyectos Ambientales
                </h1>
                <p class="text-h5 text-white mb-8">
                  Plataforma de análisis integral para la gestión y seguimiento de proyectos ambientales en Chile
                </p>
                <v-btn
                  size="x-large"
                  color="white"
                  variant="elevated"
                  to="/dashboard"
                  class="text-none px-8 py-4"
                  elevation="8"
                >
                  <v-icon class="mr-3">mdi-chart-line</v-icon>
                  Explorar Dashboard
                </v-btn>
              </div>
            </v-col>
          </v-row>

          <v-row class="features-section pa-12">
            <v-col cols="12" class="text-center mb-8">
              <h2 class="text-h3 font-weight-bold text-primary mb-4">
                Características Principales
              </h2>
              <p class="text-h6 text-grey-darken-1">
                Descubre las herramientas que te ayudarán a analizar los proyectos ambientales
              </p>
            </v-col>

            <v-col cols="12" md="4" class="mb-6">
              <v-card class="feature-card h-100" elevation="4">
                <v-card-text class="text-center pa-6">
                  <v-icon size="64" color="primary" class="mb-4">mdi-chart-bar</v-icon>
                  <h3 class="text-h5 font-weight-bold mb-3">Análisis de Proyectos</h3>
                  <p class="text-body-1 text-grey-darken-1">
                    Visualiza la evolución de proyectos ingresados vs aprobados por año con gráficos interactivos
                  </p>
                </v-card-text>
              </v-card>
            </v-col>

            <v-col cols="12" md="4" class="mb-6">
              <v-card class="feature-card h-100" elevation="4">
                <v-card-text class="text-center pa-6">
                  <v-icon size="64" color="success" class="mb-4">mdi-currency-usd</v-icon>
                  <h3 class="text-h5 font-weight-bold mb-3">Análisis de Inversión</h3>
                  <p class="text-body-1 text-grey-darken-1">
                    Explora la distribución de inversiones por año y tipo de proyecto (DIA/EIA)
                  </p>
                </v-card-text>
              </v-card>
            </v-col>

            <v-col cols="12" md="4" class="mb-6">
              <v-card class="feature-card h-100" elevation="4">
                <v-card-text class="text-center pa-6">
                  <v-icon size="64" color="warning" class="mb-4">mdi-clock-outline</v-icon>
                  <h3 class="text-h5 font-weight-bold mb-3">Tiempos de Tramitación</h3>
                  <p class="text-body-1 text-grey-darken-1">
                    Analiza los tiempos promedio de procesamiento por año y tipo de proyecto
                  </p>
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>

          <v-row class="stats-section pa-12">
            <v-col cols="12" class="text-center mb-8">
              <h2 class="text-h3 font-weight-bold text-white mb-4">
                Datos del Sistema
              </h2>
              <p class="text-h6 text-white">
                Información actualizada sobre proyectos ambientales
              </p>
            </v-col>

            <v-col cols="12" md="3" class="text-center">
              <div class="stat-item">
                <v-icon size="48" color="white" class="mb-3">mdi-file-document</v-icon>
                <div class="text-h3 font-weight-bold text-white mb-2">+2,000</div>
                <div class="text-subtitle-1 text-white">Proyectos Registrados</div>
              </div>
            </v-col>

            <v-col cols="12" md="3" class="text-center">
              <div class="stat-item">
                <v-icon size="48" color="white" class="mb-3">mdi-map</v-icon>
                <div class="text-h3 font-weight-bold text-white mb-2">16</div>
                <div class="text-subtitle-1 text-white">Regiones</div>
              </div>
            </v-col>

            <v-col cols="12" md="3" class="text-center">
              <div class="stat-item">
                <v-icon size="48" color="white" class="mb-3">mdi-calendar-range</v-icon>
                <div class="text-h3 font-weight-bold text-white mb-2">2020-2025</div>
                <div class="text-subtitle-1 text-white">Período de Análisis</div>
              </div>
            </v-col>

            <v-col cols="12" md="3" class="text-center">
              <div class="stat-item">
                <v-icon size="48" color="white" class="mb-3">mdi-chart-line</v-icon>
                <div class="text-h3 font-weight-bold text-white mb-2">3</div>
                <div class="text-subtitle-1 text-white">Tipos de Análisis</div>
              </div>
            </v-col>
          </v-row>

          <v-row class="cta-section pa-12">
            <v-col cols="12" class="text-center">
              <v-card class="cta-card" elevation="8">
                <v-card-text class="pa-8">
                  <h2 class="text-h3 font-weight-bold text-primary mb-4">
                    ¿Listo para explorar?
                  </h2>
                  <p class="text-h6 text-grey-darken-1 mb-6">
                    Accede al dashboard completo y descubre insights valiosos sobre los proyectos ambientales
                  </p>
                  <v-btn
                    size="x-large"
                    color="primary"
                    variant="elevated"
                    to="/dashboard"
                    class="text-none px-8 py-4"
                    elevation="4"
                  >
                    <v-icon class="mr-3">mdi-arrow-right</v-icon>
                    Ir al Dashboard
                  </v-btn>
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </v-container>
  </main>
</template>

<style scoped>
.home-background {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  min-height: 100vh;
}

.hero-section {
  min-height: 80vh;
  background: linear-gradient(135deg, rgba(102, 126, 234, 0.9) 0%, rgba(118, 75, 162, 0.9) 100%);
  position: relative;
}

.hero-section::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><defs><pattern id="grain" width="100" height="100" patternUnits="userSpaceOnUse"><circle cx="50" cy="50" r="1" fill="white" opacity="0.1"/></pattern></defs><rect width="100" height="100" fill="url(%23grain)"/></svg>');
  opacity: 0.3;
}

.hero-content {
  position: relative;
  z-index: 2;
}

.features-section {
  background: white;
}

.feature-card {
  border-radius: 16px;
  transition: transform 0.3s ease-in-out;
  cursor: pointer;
}

.feature-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 12px 40px rgba(0, 0, 0, 0.15) !important;
}

.stats-section {
  background: linear-gradient(135deg, #2c3e50 0%, #34495e 100%);
  position: relative;
}

.stats-section::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><defs><pattern id="dots" width="20" height="20" patternUnits="userSpaceOnUse"><circle cx="10" cy="10" r="1" fill="white" opacity="0.1"/></pattern></defs><rect width="100" height="100" fill="url(%23dots)"/></svg>');
}

.stat-item {
  position: relative;
  z-index: 2;
}

.cta-section {
  background: #f8f9fa;
}

.cta-card {
  border-radius: 16px;
  background: white;
}

@media (max-width: 768px) {
  .hero-section {
    min-height: 60vh;
  }
  
  .text-h2 {
    font-size: 2rem !important;
  }
  
  .text-h3 {
    font-size: 1.5rem !important;
  }
  
  .text-h5 {
    font-size: 1.25rem !important;
  }
  
  .pa-12 {
    padding: 48px 16px !important;
  }
}

.h-100 {
  height: 100%;
}
</style>
