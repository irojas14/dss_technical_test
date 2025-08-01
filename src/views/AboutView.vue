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
            <v-col cols="12">
              <v-card class="mb-6 content-card" elevation="4">
                <v-card-title class="d-flex align-center">
                  <v-icon class="mr-3" color="primary">mdi-file-document</v-icon>
                  Descripción del Proyecto
                </v-card-title>
                <v-card-text class="pt-4">
                  <div class="project-description">
                    <div class="description-section mb-6">
                      <h4 class="text-h6 font-weight-bold text-primary mb-3">
                        <v-icon class="mr-2" color="primary">mdi-target</v-icon>
                        Propósito
                      </h4>
                      <p class="text-body-1 mb-4">
                        Esta plataforma fue desarrollada como parte de una prueba técnica para demostrar habilidades en el desarrollo de aplicaciones web modernas utilizando <strong>Vue 3</strong> y <strong>Vuetify 3</strong>.
                      </p>
                    </div>

                    <div class="description-section mb-6">
                      <h4 class="text-h6 font-weight-bold text-primary mb-3">
                        <v-icon class="mr-2" color="primary">mdi-chart-line</v-icon>
                        Objetivo Principal
                      </h4>
                      <p class="text-body-1 mb-4">
                        Proporcionar una interfaz intuitiva y funcional para analizar y visualizar datos de proyectos ambientales en Chile, permitiendo a los usuarios explorar diferentes aspectos como:
                      </p>
                      <div class="features-grid">
                        <div class="feature-highlight mb-3">
                          <v-icon color="success" class="mr-2">mdi-trending-up</v-icon>
                          <span class="text-body-1">Evolución temporal de proyectos</span>
                        </div>
                        <div class="feature-highlight mb-3">
                          <v-icon color="info" class="mr-2">mdi-currency-usd</v-icon>
                          <span class="text-body-1">Análisis de inversiones</span>
                        </div>
                        <div class="feature-highlight mb-3">
                          <v-icon color="warning" class="mr-2">mdi-clock-outline</v-icon>
                          <span class="text-body-1">Tiempos de tramitación</span>
                        </div>
                        <div class="feature-highlight mb-3">
                          <v-icon color="primary" class="mr-2">mdi-filter-variant</v-icon>
                          <span class="text-body-1">Filtrado por región</span>
                        </div>
                      </div>
                    </div>

                    <div class="description-section mb-6">
                      <h4 class="text-h6 font-weight-bold text-primary mb-3">
                        <v-icon class="mr-2" color="primary">mdi-chart-bar</v-icon>
                        Visualización de Datos
                      </h4>
                      <p class="text-body-1 mb-4">
                        La aplicación utiliza <strong>Chart.js</strong> para la visualización de datos, proporcionando gráficos interactivos y responsivos que se adaptan a diferentes dispositivos y ofrecen una experiencia de usuario excepcional.
                      </p>
                    </div>

                    <div class="description-section">
                      <h4 class="text-h6 font-weight-bold text-primary mb-3">
                        <v-icon class="mr-2" color="primary">mdi-lightbulb</v-icon>
                        Beneficios de la Plataforma
                      </h4>
                      <p class="text-body-1">
                        Esta herramienta facilita la toma de decisiones informadas en materia ambiental, proporcionando insights valiosos sobre la evolución de proyectos, patrones de inversión y eficiencia en los procesos de tramitación ambiental en Chile.
                      </p>
                    </div>
                  </div>
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>

          <!-- Tech and Features Section -->
          <v-row>
            <v-col cols="12" md="6">
              <v-card class="mb-6 tech-card" elevation="4">
                <v-card-title class="d-flex align-center">
                  <v-icon class="mr-3" color="success">mdi-cog</v-icon>
                  Stack Tecnológico
                </v-card-title>
                <v-card-text class="pt-4">
                  <div class="tech-grid">
                    <div class="tech-item">
                      <v-icon color="primary" class="mr-2">mdi-vuejs</v-icon>
                      <div>
                        <div class="text-body-1 font-weight-bold">Vue 3</div>
                        <div class="text-caption text-grey">Composition API</div>
                      </div>
                    </div>
                    <div class="tech-item">
                      <v-icon color="primary" class="mr-2">mdi-palette</v-icon>
                      <div>
                        <div class="text-body-1 font-weight-bold">Vuetify 3</div>
                        <div class="text-caption text-grey">UI Framework</div>
                      </div>
                    </div>
                    <div class="tech-item">
                      <v-icon color="primary" class="mr-2">mdi-chart-line</v-icon>
                      <div>
                        <div class="text-body-1 font-weight-bold">Chart.js</div>
                        <div class="text-caption text-grey">Visualización</div>
                      </div>
                    </div>
                    <div class="tech-item">
                      <v-icon color="primary" class="mr-2">mdi-language-typescript</v-icon>
                      <div>
                        <div class="text-body-1 font-weight-bold">TypeScript</div>
                        <div class="text-caption text-grey">Tipado Estático</div>
                      </div>
                    </div>
                    <div class="tech-item">
                      <v-icon color="primary" class="mr-2">mdi-router</v-icon>
                      <div>
                        <div class="text-body-1 font-weight-bold">Vue Router</div>
                        <div class="text-caption text-grey">Navegación SPA</div>
                      </div>
                    </div>
                  </div>
                </v-card-text>
              </v-card>
            </v-col>

            <v-col cols="12" md="6">
              <v-card class="mb-6 features-card" elevation="4">
                <v-card-title class="d-flex align-center">
                  <v-icon class="mr-3" color="info">mdi-star</v-icon>
                  Características Principales
                </v-card-title>
                <v-card-text class="pt-4">
                  <div class="features-list">
                    <div class="feature-item">
                      <v-icon color="success" class="mr-2">mdi-check-circle</v-icon>
                      <div>
                        <div class="text-body-1 font-weight-bold">Diseño Responsivo</div>
                        <div class="text-caption text-grey">Adaptable a todos los dispositivos</div>
                      </div>
                    </div>
                    <div class="feature-item">
                      <v-icon color="success" class="mr-2">mdi-check-circle</v-icon>
                      <div>
                        <div class="text-body-1 font-weight-bold">Filtros Dinámicos</div>
                        <div class="text-caption text-grey">Búsqueda avanzada de datos</div>
                      </div>
                    </div>
                    <div class="feature-item">
                      <v-icon color="success" class="mr-2">mdi-check-circle</v-icon>
                      <div>
                        <div class="text-body-1 font-weight-bold">Gráficos Interactivos</div>
                        <div class="text-caption text-grey">Visualización dinámica</div>
                      </div>
                    </div>
                    <div class="feature-item">
                      <v-icon color="success" class="mr-2">mdi-check-circle</v-icon>
                      <div>
                        <div class="text-body-1 font-weight-bold">Carga de Datos JSON</div>
                        <div class="text-caption text-grey">Integración con APIs</div>
                      </div>
                    </div>
                    <div class="feature-item">
                      <v-icon color="success" class="mr-2">mdi-check-circle</v-icon>
                      <div>
                        <div class="text-body-1 font-weight-bold">Navegación SPA</div>
                        <div class="text-caption text-grey">Experiencia fluida</div>
                      </div>
                    </div>
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
  border-radius: 0;
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
  border-radius: 0;
  border-left: 4px solid #1976d2;
}

.tech-card {
  background: white;
  border-radius: 0;
  border-left: 4px solid #4caf50;
}

.features-card {
  background: white;
  border-radius: 0;
  border-left: 4px solid #2196f3;
}

.footer-card {
  background: white;
  border-radius: 0;
  border-left: 4px solid #ff9800;
}

.description-section {
  margin-bottom: 2rem;
}

.features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1rem;
  margin-top: 1rem;
}

.feature-highlight {
  display: flex;
  align-items: center;
  padding: 0.75rem;
  background: rgba(25, 118, 210, 0.05);
  border-radius: 8px;
  border-left: 3px solid #1976d2;
}

.tech-grid {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.tech-item {
  display: flex;
  align-items: center;
  padding: 0.75rem;
  background: rgba(76, 175, 80, 0.05);
  border-radius: 8px;
  border-left: 3px solid #4caf50;
}

.features-list {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.feature-item {
  display: flex;
  align-items: flex-start;
  padding: 0.75rem;
  background: rgba(33, 150, 243, 0.05);
  border-radius: 8px;
  border-left: 3px solid #2196f3;
}

.v-card {
  border-radius: 0;
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
  
  .features-grid {
    grid-template-columns: 1fr;
  }
}
</style>
