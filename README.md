# 🚀 GCP E-Commerce Analytics Pipeline & Dashboard

![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![Google Cloud Platform](https://img.shields.io/badge/Google_Cloud-4285F4?style=for-the-badge&logo=googlecloud&logoColor=white)
![BigQuery](https://img.shields.io/badge/BigQuery-669DF6?style=for-the-badge&logo=google&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-003B57?style=for-the-badge&logo=postgresql&logoColor=white)

> 🤖 **Deploy Automatically with AI Agents:** Want to deploy this entire GCS + BigQuery pipeline into your own Google Cloud project in one command using **Claude Code, Cursor, Codex CLI, or Gemini CLI**?  
> 👉 **[Get the ready-to-run AI Agent Skill on Agensi.io](https://www.agensi.io/skills/gcp-e-commerce-analytics-pipeline-bigquery-gcs)** (includes automated `deploy_pipeline.sh`, parameterized regions, international `vw_clean_sales` & `vw_kpi_summary` SQL views, and sample USD datasets).

## 📌 Project Overview

This project builds an end-to-end cloud analytics pipeline implemented on **Google Cloud Platform (GCP)** for ingesting, cleaning, and visualizing e-commerce transaction records.

Using **Google Cloud Storage (GCS)**, **BigQuery**, and **Power BI Desktop**, raw CSV sales logs were transformed into a clean analytical view to deliver an executive dark-mode dashboard tracking revenue, transaction volume, and geographic performance.

## 🖼️ Dashboard Preview

<img width="1058" height="594" alt="dashboard_preview (2)" src="https://github.com/user-attachments/assets/fb5d1e07-3502-487e-bc89-1bf81c9b6ff3" />

## 🛠️ Tech Stack & Architecture

- **Google Cloud Storage (GCS):** Staging layer for raw e-commerce CSV datasets hosted in the `southamerica-west1` region.
- **Google BigQuery (Data Warehouse):** Large-scale data ingestion into the `ventas` table and SQL transformation via analytical views (`vw_ventas_limpias`).
- **Power BI Desktop:** Analytical data modeling and interactive dark-mode executive dashboard design.

```text
[ Raw CSV Files ] ──► [ GCS Bucket (southamerica-west1) ] ──► [ BigQuery SQL View ] ──► [ Power BI Dashboard ]
```

## 📊 Pipeline & Data Modeling Highlights
The analytical workflow separates raw storage from business-ready reporting views in BigQuery:
1. Raw Ingestion: Uploaded raw transactional CSV files to a dedicated Cloud Storage bucket (southamerica-west1).
2. SQL Transformation Layer: Loaded records into BigQuery (ventas) and created the curated view vw_ventas_limpias to filter data inconsistencies, standardize schema types, and optimize query performance.
3. Executive Visualization: Connected BigQuery to Power BI to monitor financial KPIs (Total Revenue, Transaction Volume) alongside regional and time-series breakdowns.

```sql
-- Example: Curated analytical view in BigQuery
CREATE OR REPLACE VIEW `ecommerce_dw.vw_ventas_limpias` AS
SELECT
    transaction_id,
    CAST(transaction_date AS DATE) AS fecha_venta,
    country,
    product_category,
    SAFE_CAST(revenue AS FLOAT64) AS monto_ingreso
FROM `ecommerce_dw.ventas`
WHERE revenue > 0 AND transaction_id IS NOT NULL;
```

## 💡 Key Business & Technical Insights
1. Cloud-to-BI Decoupling: Centralizing data cleansing in BigQuery (vw_ventas_limpias) eliminated heavy local transformations in Power Query and ensured consistent metric definitions.
2. Financial & Geographic Visibility: Enabled instant tracking of top-performing regions, seasonal revenue trends, and transaction distribution through interactive filtering.
3. Executive Dark-Mode Storytelling: Designed a high-contrast visual layout tailored for rapid executive review of core commercial KPIs.

## 📁 Repository Structure
```text
├── GCP_Ecommerce_Analytics.pbix   # Interactive Power BI report file
└── README.md                      # Pipeline architecture and project documentation
```
