# Plataforma de Análisis de Proyectos Ambientales

Una aplicación web moderna desarrollada con **Vue 3** y **Vuetify 3** para el análisis y visualización de datos de proyectos ambientales en Chile.

## 🚀 Características Principales

- **Dashboard Interactivo**: Visualización de datos en tiempo real con gráficos responsivos
- **Análisis Multi-dimensional**: Proyectos ingresados vs aprobados, inversiones y tiempos de tramitación
- **Filtros Avanzados**: Por región, año y tipo de proyecto
- **Carga de Datos Personalizada**: Soporte para archivos JSON personalizados
- **Diseño Responsivo**: Optimizado para desktop, tablet y smartphone
- **Interfaz Intuitiva**: Navegación clara y moderna

## 📋 Requisitos Previos

- Node.js (versión 16 o superior)
- npm o yarn

## 🛠️ Instalación y Configuración

### 1. Clonar el Repositorio
```bash
git clone <url-del-repositorio>
cd dss_technical_test
```

### 2. Instalar Dependencias
```bash
npm install
```

### 3. Ejecutar en Modo Desarrollo
```bash
npm run dev
```

La aplicación estará disponible en `http://localhost:5173`

## 📖 Guía de Uso

### 🏠 Página de Inicio (Home)

La página principal presenta:
- **Título de la aplicación** con navegación
- **Botón "Explorar Dashboard"** para acceder al análisis
- **Información general** sobre la plataforma

### 📊 Página Dashboard

#### **1. Selección de Fuente de Datos**
Al cargar la página por primera vez, se mostrará un modal con dos opciones:

- **Datos por Defecto**: Utiliza el archivo JSON incluido en el proyecto
- **Subir Archivo JSON**: Permite cargar un archivo JSON personalizado

> **Nota**: El archivo JSON debe tener el mismo formato que el incluido por defecto.

#### **2. Navegación del Dashboard**

**Barra de Filtros:**
- **Dashboard a Mostrar**: Selecciona entre:
  - Todos los Dashboards
  - Proyectos Ingresados vs Aprobados
  - Inversión por Año y Tipo
  - Tiempo de Tramitación
- **Filtrar por Región**: Filtra proyectos por región específica
- **Filtrar por Año**: Filtra proyectos por año específico

#### **3. Dashboards Disponibles**

##### **📈 Proyectos Ingresados vs Aprobados**
- **Descripción**: Muestra la evolución temporal de proyectos ambientales
- **Datos**: Cantidad de proyectos ingresados y aprobados por año
- **Visualización**: Gráfico de barras con dos series de datos

##### **💰 Inversión por Año y Tipo**
- **Descripción**: Análisis de inversiones agrupadas por año y tipo
- **Datos**: Suma de inversiones por año y tipo (DIA/EIA)
- **Visualización**: Gráfico de barras apiladas

##### **⏱️ Tiempo de Tramitación**
- **Descripción**: Análisis de eficiencia en tiempos de tramitación
- **Datos**: Diferencia entre fecha de ingreso y fecha de resolución
- **Visualización**: Gráfico de líneas mostrando días promedio

#### **4. Estadísticas Generales**

En la parte inferior se muestran cuatro tarjetas con estadísticas:
- **Total Proyectos**: Número total de proyectos en el dataset
- **Proyectos Aprobados**: Cantidad de proyectos con estado "Aprobado"
- **Regiones**: Número de regiones únicas
- **Días Promedio**: Tiempo promedio de tramitación

### ℹ️ Página About

Contiene información detallada sobre:
- **Propósito del proyecto**
- **Stack tecnológico utilizado**
- **Características principales**
- **Beneficios de la plataforma**

## 📱 Responsividad

La aplicación está optimizada para diferentes dispositivos:

### **Desktop (> 768px)**
- Navegación completa con botones
- Gráficos de tamaño completo
- Información detallada visible

### **Tablet (≤ 768px)**
- Tamaños de fuente ajustados
- Gráficos responsivos
- Navegación adaptada

### **Smartphone (≤ 480px)**
- Menú hamburguesa para navegación
- Gráficos optimizados para pantalla pequeña
- Textos y botones redimensionados

## 🔧 Tecnologías Utilizadas

- **Frontend**: Vue 3 (Composition API)
- **UI Framework**: Vuetify 3
- **Gráficos**: Chart.js
- **Lenguaje**: TypeScript
- **Build Tool**: Vite
- **Estilos**: CSS3 con media queries

## 📁 Estructura del Proyecto

```
src/
├── components/
│   ├── charts/           # Componentes de gráficos
│   └── DashboardView.vue # Vista principal del dashboard
├── views/
│   ├── HomeView.vue      # Página de inicio
│   └── AboutView.vue     # Página de información
├── router/               # Configuración de rutas
└── assets/               # Estilos y recursos
```

## 🚀 Comandos Disponibles

```bash
# Desarrollo
npm run dev

# Construcción para producción
npm run build

# Verificación de tipos
npm run type-check

# Linting
npm run lint
```

## 📊 Formato de Datos

El archivo JSON debe contener un array de objetos con la siguiente estructura:

```json
[
  {
    "id": "string",
    "nombre": "string",
    "fecha": "DD-MM-YYYY",
    "fecha_resolucion": "DD-MM-YYYY" | null,
    "estado": "string",
    "tipo": "DIA" | "EIA",
    "region": "string",
    "inversion": "string (número con formato)"
  }
]
```

## 🎯 Casos de Uso

### **Para Evaluadores Técnicos:**
1. **Revisar la responsividad**: Probar en diferentes tamaños de pantalla
2. **Verificar funcionalidad**: Probar todos los dashboards y filtros
3. **Evaluar UX**: Navegar por todas las páginas
4. **Probar carga de datos**: Subir un archivo JSON personalizado

### **Para Usuarios Finales:**
1. **Explorar datos**: Usar los filtros para analizar diferentes aspectos
2. **Comparar métricas**: Revisar estadísticas entre diferentes años/regiones
3. **Exportar insights**: Tomar capturas de pantalla de gráficos relevantes

## 🔍 Funcionalidades Destacadas

- ✅ **Análisis temporal** de proyectos ambientales
- ✅ **Visualización de inversiones** por tipo de proyecto
- ✅ **Métricas de eficiencia** en tramitación
- ✅ **Filtros dinámicos** por región y año
- ✅ **Carga de datos personalizada**
- ✅ **Diseño completamente responsivo**
- ✅ **Interfaz moderna e intuitiva**

---

**Desarrollado con ❤️ usando Vue 3 y Vuetify 3**
