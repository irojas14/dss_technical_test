<script setup lang="ts">
import { RouterView } from 'vue-router'
</script>

<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <v-container class="d-flex align-center">
        <v-app-bar-title class="text-h5 app-title">
          Proyectos Ambientales
        </v-app-bar-title>
        <v-spacer></v-spacer>
        <div class="d-none d-md-flex">
          <v-btn to="/" variant="text" class="text-none">
            Inicio
          </v-btn>
          <v-btn to="/dashboard" variant="text" class="text-none">
            Dashboard
          </v-btn>
          <v-btn to="/about" variant="text" class="text-none">
            Acerca de
          </v-btn>
        </div>
        <v-menu class="d-md-none">
          <template v-slot:activator="{ props }">
            <v-btn
              icon
              v-bind="props"
              class="d-md-none"
            >
              <v-icon>mdi-menu</v-icon>
            </v-btn>
          </template>
          <v-list>
            <v-list-item to="/" prepend-icon="mdi-home">
              <v-list-item-title>Inicio</v-list-item-title>
            </v-list-item>
            <v-list-item to="/dashboard" prepend-icon="mdi-chart-line">
              <v-list-item-title>Dashboard</v-list-item-title>
            </v-list-item>
            <v-list-item to="/about" prepend-icon="mdi-information">
              <v-list-item-title>Acerca de</v-list-item-title>
            </v-list-item>
          </v-list>
        </v-menu>
      </v-container>
    </v-app-bar>

    <v-main class="main-content">
      <RouterView />
    </v-main>
  </v-app>
</template>

<style scoped>
.v-btn {
  text-transform: none;
}

.main-content {
  width: 100% !important;
  max-width: 100% !important;
  padding: 0 !important;
}

@media (max-width: 768px) {
  .app-title {
    font-size: 1.25rem !important;
  }
}

@media (max-width: 480px) {
  .app-title {
    font-size: 1rem !important;
  }
}
</style>
