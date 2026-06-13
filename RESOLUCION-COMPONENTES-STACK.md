**Prometheus:** Recolecta metricas en formato Pull desde `/metrics` de las aplicaciones y exporters comonode-exporter, cAdvisor, las almacena en serie temporal con retention configurado.

**Loki:** Almacena logs en formato JSON sin indexar cada línea, solo por etiquetas (tier, service, container), es eficiente para búsquedas rápidas de logs.

**Grafana Alloy:** Agente de recolección de logs que descubre contenedores vía Docker socket, parsea JSON y los envía a Loki etiquetados por tier y servicio.

**Grafana:** Plataforma de visualización que consulta Prometheus para métricas y Loki para logs, permite crear dashboards y configurar alertas con umbrales.

**node-exporter:** Exporta métricas del sistema operativo como CPU, memoria, disco, red del host donde corre, Prometheus las scrapea para monitoreo infraestructura.

**cAdvisor:** Monitorea recursos de contenedores como Docker CPU, memoria, filesystem, red y expone métricas por contenedor, integrado con Prometheus para observabilidad de aplicaciones.

**Backend/Frontend:** Aplicaciones Node.js instrumentadas con prom-client, exponen `/metrics` con métricas de aplicación y emiten logs estructurados que Alloy recolecta.