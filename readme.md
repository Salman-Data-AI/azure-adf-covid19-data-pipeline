# Azure ADF COVID-19 Data Pipeline

This repository contains an end-to-end Azure Data Factory (ADF) implementation of a COVID-19 analytics pipeline using data from the ECDC website and Azure Blob Storage.

## 🌐 Project Overview

- **Objective:** Automate ingestion, transformation, and loading of COVID-19 data for analytics and visualization in Power BI.
- **Tech Stack:** Azure Data Factory, Azure Blob Storage, Azure Data Lake Gen2, Azure SQL Database, Azure Databricks, Power BI.

## 📊 Architecture

The solution follows a layered medallion architecture:

- **Extract Layer:** Fetches raw data from APIs and Blob storage
- **Transform Layer:** Cleans and reshapes data via ADF Data Flows and Databricks
- **Load Layer:** Pushes processed data into Azure SQL Database
- **Analytics Layer:** Visualizes the data in Power BI and supports ML tasks

<p align="center">
  <img src="architecture/adf_project_architecture.png" width="700"/>
</p>

## 🏗️ Components

### Pipelines
- Organized under: `pipelines/`
- Subfolders: Extract, Transform, Load, Execute, Misc

### Datasets
- Raw, Processed, Lookup, Metadata, Loaded datasets for each data source

### Data Flows
- df_transform_cases_deaths
- df_transform_hospital_admissions
- df_transform_testing

### SQL Scripts
- `sql/create_tables.sql`: Table creation for Azure SQL DB
- `sql/load_data_statements.sql`: Data insertion scripts

### Documentation
- `Azure Data Factory (ADF) Notes.pdf`: Detailed ADF hands-on guide
- `ADF_pipeline_structure.jpg`: Screenshot of folder structure

## 📈 Data Sources

- **ECDC API** – Cases & Deaths, Hospital Admissions, Testing
- **Azure Blob** – Population file

## 🛠️ Key Activities & Transformations

- **Copy Data, Validation, Get Metadata, If Condition**
- **Data Flows:** Pivot, Select, Lookup, Conditional Split, Aggregate, Sort
- **Orchestration:** Execute Pipeline, Tumbling Window Triggers
- **Monitoring:** ADF Pipeline Monitor & Alerts

## 📊 Power BI Integration

Processed data is visualized using Power BI for trend analysis and reporting.

---

## 📚 References

- [Azure Data Factory Documentation](https://learn.microsoft.com/en-us/azure/data-factory/)
- ECDC COVID-19 Dataset

---

## 🧠 Author

Created by @salman-data-ai
