# Stack de Monitoreo con Prometheus, Grafana, Alertmanager, Node Exporter y cAdvisor

Este proyecto proporciona un stack completo de monitoreo para sistemas y contenedores usando Docker Compose. Incluye Prometheus para la recolección de métricas, Grafana para visualización, Alertmanager para gestión de alertas, Node Exporter para métricas del sistema y cAdvisor para métricas de contenedores.

## Servicios Incluidos

- **Prometheus**: Recolección y almacenamiento de métricas.
- **Grafana**: Visualización de métricas y dashboards.
- **Alertmanager**: Gestión y envío de alertas.
- **Node Exporter**: Exporta métricas del sistema operativo.
- **cAdvisor**: Exporta métricas de contenedores Docker.

## Estructura del Proyecto

```
.
├── alertmanager/
│   └── config.yml
├── grafana/
│   └── provisioning/
│       ├── dashboards/
│       │   ├── dashboards.yml
│       │   └── grafana/
│       │       └── dashboards/
│       │           └── system-overview.json
│       └── datasources/
│           └── datasource.yml
├── prometheus/
│   ├── prometgeus.yml
│   └── rules/
│       ├── container_alerts.yml
│       ├── node_alerts.yml
│       └── recording_rules.yml
└── docker.compose.yaml
```

## Requisitos

- Docker
- Docker Compose

## Uso

1. **Clona este repositorio:**
   ```sh
   git clone https://github.com/tu-usuario/tu-repo.git
   cd tu-repo
   ```

2. **Inicia los servicios:**
   ```sh
   docker compose up -d
   ```

3. **Accede a las interfaces:**
   - Prometheus: [http://localhost:9090](http://localhost:9090)
   - Grafana: [http://localhost:3000](http://localhost:3000) (usuario: `admin`, contraseña: `admin`)
   - Alertmanager: [http://localhost:9093](http://localhost:9093)

## Dashboards y Alertas

- Los dashboards de Grafana están preconfigurados y se cargan automáticamente.
- Las reglas de alertas para Prometheus están en `prometheus/rules/`.
- La configuración de Alertmanager se encuentra en `alertmanager/config.yml`.

## Personalización

- Puedes agregar o modificar dashboards en `grafana/provisioning/dashboards/`.
- Para agregar nuevas reglas de alertas, edita los archivos en `prometheus/rules/`.

## Licencia

MIT

---

> Proyecto desarrollado para monitoreo de sistemas y contenedores con tecnologías open