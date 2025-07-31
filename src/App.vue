<script setup lang="ts">
import { RouterView } from 'vue-router'
</script>

<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <v-container class="d-flex align-center">
        <v-app-bar-title class="text-h5">
          Proyectos Ambientales
        </v-app-bar-title>
        <v-spacer></v-spacer>
        <v-btn to="/" variant="text" class="text-none">
          Inicio
        </v-btn>
        <v-btn to="/dashboard" variant="text" class="text-none">
          Dashboard
        </v-btn>
        <v-btn to="/about" variant="text" class="text-none">
          Acerca de
        </v-btn>
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
</style>
