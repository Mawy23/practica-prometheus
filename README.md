# Proyecto de Monitoreo con Prometheus y Grafana

Este repositorio contiene un proyecto de monitoreo utilizando **Prometheus**, **Grafana** y otros servicios relacionados. El objetivo es configurar un entorno de monitoreo para recopilar métricas de servicios y recursos de cómputo.

## Estructura del Proyecto

- **`docker-compose.yml`**: Archivo de configuración para levantar los servicios necesarios con Docker Compose.
- **`prometheus.yml`**: Configuración de Prometheus para definir los trabajos de scraping y las métricas a recolectar.
- **`Consultas API-1744035032084.json`**: Dashboard de Grafana para visualizar métricas relacionadas con las consultas a la API.
- **`Recursos de Cómputo-1744035053128.json`**: Dashboard de Grafana para monitorear recursos de cómputo como CPUs y almacenamiento.

## Servicios Incluidos

### 1. Prometheus
- **Imagen**: `prom/prometheus`
- **Puerto**: `9090`
- **Configuración**: Utiliza el archivo `prometheus.yml` para definir los trabajos de scraping.

### 2. Grafana
- **Imagen**: `grafana/grafana:latest`
- **Puerto**: `3000`
- **Dashboards**:
  - **Consultas API**: Métricas de rendimiento de solicitudes HTTP.
  - **Recursos de Cómputo**: Monitoreo de CPUs y almacenamiento.

### 3. Node Exporter
- **Imagen**: `prom/node-exporter`
- **Puerto**: `9100`
- **Función**: Exporta métricas del sistema operativo.

### 4. Servicios Demo
- **Imágenes**: `docker.io/julius/prometheus-demo-service:latest`
- **Puertos**:
  - `10000:8080`
  - `20000:8080`
  - `30000:8080`
- **Función**: Servicios de ejemplo para generar métricas.

## Configuración

### Prometheus
El archivo [`prometheus.yml`](prometheus.yml) define los trabajos de scraping:
- **`prometheus`**: Monitorea el propio Prometheus.
- **`prometheus-service-demo`**: Monitorea los servicios demo.
- **`node`**: Monitorea el Node Exporter.

### Dashboards de Grafana
Los dashboards están definidos en los archivos JSON:
- **Consultas API**: Métricas de rendimiento de solicitudes HTTP.
- **Recursos de Cómputo**: Monitoreo de CPUs y almacenamiento.

## Cómo Usar

1. Clona este repositorio:

   git clone https://github.com/Mawy23/practica-prometheus.git

2. Levanta los servicios con Docker Compose:

   docker-compose up -d

3. Accede a los servicios:

  - Prometheus: http://localhost:9090
  - Grafana: http://localhost:3000 (usuario: admin, contraseña: admin por defecto)

4. Importa los dashboards en Grafana:

  - Ve a Dashboards > Import.
  - Carga los archivos JSON de los dashboards.

Métricas Recolectadas
  - Consultas API
    - Percentiles P90 y P95 de duración de solicitudes HTTP.
    - Promedio de duración de solicitudes HTTP en los últimos 5 minutos.

  - Recursos de Cómputo
    - Número de CPUs disponibles.
    - Porcentaje de uso del sistema de archivos en /.

  - Requisitos
    - Docker y Docker Compose instalados.
    - Acceso a los puertos 9090, 3000, y 9100.
  
