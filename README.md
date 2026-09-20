# 🚀 GCP E-Commerce Analytics Pipeline & Dashboard

Pipeline de datos End-to-End implementado en Google Cloud Platform (GCP) para el procesamiento, limpieza y visualización analítica de datos de transacciones de comercio electrónico.

## 🏗️ Arquitectura y Tecnologías
* **Cloud Storage:** Almacenamiento RAW de archivos de origen en formato CSV.
* **BigQuery (Data Warehouse):** Ingesta de datos masivos y creación de capa limpia mediante Vistas SQL (`vw_ventas_limpias`).
* **Power BI Desktop:** Modelado de datos y desarrollo de dashboard ejecutivo en Modo Oscuro.
* **Git & GitHub:** Control de versiones y despliegue del proyecto.

## 📊 Descripción del Pipeline
1. **Ingesta (RAW):** Carga del dataset original en un bucket de Cloud Storage en la región `southamerica-west1`.
2. **Procesamiento (SQL):** Ingesta hacia BigQuery en la tabla `ventas` y modelado analítico a través de la vista `vw_ventas_limpias`, filtrando inconsistencias y casteando tipos de datos de forma eficiente.
3. **Visualización:** Reporte interactivo con KPIs financieros (Ingresos totales, Transacciones) y desglose geográfico/temporal.

## 📂 Estructura del Repositorio
- `GCP_Ecommerce_Analytics.pbix`: Archivo del reporte interactivo en Power BI.
