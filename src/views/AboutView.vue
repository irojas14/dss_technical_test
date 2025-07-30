<script setup lang="ts">
// Componente About mejorado
</script>

<template>
  <v-main class="about-background">
    <v-container fluid class="pa-0">
      <v-row>
        <v-col cols="12">
          <!-- Header Section -->
          <v-row>
            <v-col cols="12">
              <v-card class="mb-6 about-header-card" elevation="8">
                <v-card-title class="text-h3 text-center py-6">
                  <v-icon size="48" class="mr-4" color="primary">mdi-information</v-icon>
                  Acerca de Proyectos Ambientales
                </v-card-title>
                <v-card-subtitle class="text-h6 text-center pb-4">
                  Plataforma de análisis y visualización de datos ambientales
                </v-card-subtitle>
              </v-card>
            </v-col>
          </v-row>

          <!-- Content Section -->
          <v-row>
            <v-col cols="12" md="8">
              <v-card class="mb-6 content-card" elevation="4">
                <v-card-title class="d-flex align-center">
                  <v-icon class="mr-3" color="primary">mdi-file-document</v-icon>
                  Descripción del Proyecto
                </v-card-title>
                <v-card-text class="pt-4">
                  <p class="text-body-1 mb-4">
                    Esta plataforma fue desarrollada como parte de una prueba técnica para demostrar habilidades en el desarrollo de aplicaciones web modernas utilizando Vue 3 y Vuetify 3.
                  </p>
                  <p class="text-body-1 mb-4">
                    El objetivo principal es proporcionar una interfaz intuitiva y funcional para analizar y visualizar datos de proyectos ambientales en Chile, permitiendo a los usuarios explorar diferentes aspectos como:
                  </p>
                  <ul class="text-body-1 mb-4">
                    <li>Evolución temporal de proyectos ingresados vs aprobados</li>
                    <li>Análisis de inversiones por tipo de proyecto (DIA/EIA)</li>
                    <li>Tiempos promedio de tramitación</li>
                    <li>Filtrado por región y período temporal</li>
                  </ul>
                  <p class="text-body-1">
                    La aplicación utiliza tecnologías modernas como Chart.js para la visualización de datos, proporcionando gráficos interactivos y responsivos que se adaptan a diferentes dispositivos.
                  </p>
                </v-card-text>
              </v-card>
            </v-col>

            <v-col cols="12" md="4">
              <v-card class="mb-6 tech-card" elevation="4">
                <v-card-title class="d-flex align-center">
                  <v-icon class="mr-3" color="success">mdi-cog</v-icon>
                  Tecnologías Utilizadas
                </v-card-title>
                <v-card-text class="pt-4">
                  <div class="tech-item mb-3">
                    <v-icon color="primary" class="mr-2">mdi-vuejs</v-icon>
                    <span class="text-body-1">Vue 3 (Composition API)</span>
                  </div>
                  <div class="tech-item mb-3">
                    <v-icon color="primary" class="mr-2">mdi-palette</v-icon>
                    <span class="text-body-1">Vuetify 3</span>
                  </div>
                  <div class="tech-item mb-3">
                    <v-icon color="primary" class="mr-2">mdi-chart-line</v-icon>
                    <span class="text-body-1">Chart.js</span>
                  </div>
                  <div class="tech-item mb-3">
                    <v-icon color="primary" class="mr-2">mdi-language-typescript</v-icon>
                    <span class="text-body-1">TypeScript</span>
                  </div>
                  <div class="tech-item mb-3">
                    <v-icon color="primary" class="mr-2">mdi-router</v-icon>
                    <span class="text-body-1">Vue Router</span>
                  </div>
                </v-card-text>
              </v-card>

              <v-card class="mb-6 features-card" elevation="4">
                <v-card-title class="d-flex align-center">
                  <v-icon class="mr-3" color="info">mdi-star</v-icon>
                  Características
                </v-card-title>
                <v-card-text class="pt-4">
                  <div class="feature-item mb-3">
                    <v-icon color="success" class="mr-2">mdi-check-circle</v-icon>
                    <span class="text-body-1">Diseño Responsivo</span>
                  </div>
                  <div class="feature-item mb-3">
                    <v-icon color="success" class="mr-2">mdi-check-circle</v-icon>
                    <span class="text-body-1">Filtros Dinámicos</span>
                  </div>
                  <div class="feature-item mb-3">
                    <v-icon color="success" class="mr-2">mdi-check-circle</v-icon>
                    <span class="text-body-1">Gráficos Interactivos</span>
                  </div>
                  <div class="feature-item mb-3">
                    <v-icon color="success" class="mr-2">mdi-check-circle</v-icon>
                    <span class="text-body-1">Carga de Datos JSON</span>
                  </div>
                  <div class="feature-item mb-3">
                    <v-icon color="success" class="mr-2">mdi-check-circle</v-icon>
                    <span class="text-body-1">Navegación SPA</span>
                  </div>
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>

          <!-- Footer Section -->
          <v-row>
            <v-col cols="12">
              <v-card class="footer-card" elevation="4">
                <v-card-text class="text-center pa-6">
                  <v-icon size="48" color="primary" class="mb-4">mdi-heart</v-icon>
                  <h3 class="text-h5 font-weight-bold text-primary mb-3">
                    Desarrollado con ❤️ para la gestión ambiental
                  </h3>
                  <p class="text-body-1 text-grey-darken-1">
                    Esta aplicación demuestra el potencial de las tecnologías web modernas para crear herramientas útiles y accesibles para el análisis de datos ambientales.
                  </p>
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </v-container>
  </v-main>
</template>

<style scoped>
.about-background {
  background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
  min-height: 100vh;
}

.about-header-card {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  border-radius: 16px;
}

.about-header-card .v-card-title {
  color: white !important;
  font-weight: 700;
}

.about-header-card .v-card-subtitle {
  color: rgba(255, 255, 255, 0.9) !important;
}

.content-card {
  background: white;
  border-radius: 16px;
  border-left: 4px solid #1976d2;
}

.tech-card {
  background: white;
  border-radius: 16px;
  border-left: 4px solid #4caf50;
}

.features-card {
  background: white;
  border-radius: 16px;
  border-left: 4px solid #2196f3;
}

.footer-card {
  background: white;
  border-radius: 16px;
  border-left: 4px solid #ff9800;
}

.tech-item, .feature-item {
  display: flex;
  align-items: center;
  padding: 8px 0;
}

.v-card {
  border-radius: 16px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
  overflow: hidden;
}

.v-card-title {
  color: #1976d2;
  font-weight: 600;
  padding: 24px 24px 16px 24px;
}

.v-card-text {
  padding: 0 24px 24px 24px;
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .v-container {
    padding: 16px !important;
  }
  
  .v-card-title {
    font-size: 1.5rem !important;
  }
}
</style>
