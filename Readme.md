# Stack de Monitoreo con Prometheus, Grafana, Alertmanager, Node Exporter y cAdvisor

Este proyecto proporciona un stack completo de monitoreo para sistemas y contenedores usando Docker Compose. Incluye Prometheus para la recolección de métricas, Grafana para visualización, Alertmanager para gestión de alertas, Node Exporter para métricas del sistema y cAdvisor para métricas de contenedores.

## Servicios Incluidos

- **Prometheus**: Gestiona la recopilación y el almacenamiento de datos de series temporales. Extrae métricas de los exportadores y otros endpoints según su configuración. El --web.enable-lifecycleindicador le permite activar recargas de configuración sin reiniciar el contenedor.

- **Grafana**: Visualización de métricas y dashboards. Se basa en Prometheus y ofrece una interfaz intuitiva para visualizar tus datos. Las carpetas de aprovisionamiento ( datasourcesy dashboards) garantizan que todo se configure automáticamente en la primera ejecución.

- **Alertmanager**: Gestión y envío de alertas. Recibe alertas de Prometheus y las envía al lugar correcto: Slack, PagerDuty, correo electrónico, etc. Montar la configuración desde su carpeta local facilita su ajuste a medida que evolucionan sus necesidades de alerta.

- **Node Exporter**: recopila métricas de bajo nivel del sistema del host, como el uso de CPU, la memoria y las estadísticas del disco. Utilizamos el modo de montaje /procy /syssolo lectura para que Prometheus pueda extraer métricas precisas del host sin afectar el sistema.

- **cAdvisor**: se centra en las métricas a nivel de contenedor y ofrece información sobre el uso de recursos por contenedor, lo cual resulta útil cuando se ejecutan varios servicios en el mismo host.

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
   cd Stack-de-Monitoreo
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
