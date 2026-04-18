# azure-renewable-energy-etl
# Renewable Energy Telemetry ETL Pipeline

## Brief Overview
An automated cloud data pipeline that ingests, processes, and aggregates renewable energy telemetry data (solar irradiance and wind speed). Built on Azure using the Medallion Architecture, this project transforms raw simulated weather events into query-ready Delta tables for business intelligence and forecasting.

## Architecture Flow
```mermaid
graph LR
    A[Python Data Generator] -->|Uploads CSV| B[(Azure Data Lake Gen2)]
    B --> C[Azure Databricks]
    C -->|PySpark| D[Delta Lake]
    E[Azure Data Factory] -.->|Orchestrates/Triggers| C
    D --> F[Power BI / Analytics]
    
    style A fill:#f9f,stroke:#333,stroke-width:2px
    style B fill:#add8e6,stroke:#333,stroke-width:2px
    style C fill:#fcebc4,stroke:#333,stroke-width:2px
    style E fill:#d3ffd3,stroke:#333,stroke-width:2px
```

## Tech Stack
Cloud Storage: Azure Data Lake Storage Gen2 (ADLS Gen2)

Compute / Data Processing: Azure Databricks, PySpark, Spark SQL

Orchestration: Azure Data Factory (ADF)

Storage Format: Delta Lake / Parquet

Language: Python 3.x
