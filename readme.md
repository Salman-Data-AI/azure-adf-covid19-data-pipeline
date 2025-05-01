# Azure ADF COVID-19 Data Pipeline

This repository contains an end-to-end Azure Data Factory (ADF) implementation of a COVID-19 analytics pipeline using data from the ECDC website and Azure Blob Storage.

## 🌐 Project Overview

- **Objective:** Automate ingestion, transformation, and loading of COVID-19 data for analytics and visualization in Power BI.
- **Tech Stack:** Azure Data Factory, Azure Blob Storage, Azure Data Lake Gen2, Azure SQL Database, Azure Databricks, Power BI.

### Key highlights of this project include:

Automated ingestion of COVID-19 datasets (cases & deaths, hospital admissions, testing data) from the ECDC website using parameterized pipelines.

- Raw, Processed, and Curated zone management using Azure Data Lake Gen2 following a medallion architecture pattern.
- Transformation pipelines using ADF Data Flows and Azure Databricks for heavy reshaping and pivoting of data.
- Dimensional modeling by generating date_dim and country_dim lookup tables.
- Loading transformed data into Azure SQL Database and visualizing it using Power BI dashboards.
- Support for dynamic parameterization, triggers, monitoring, and pipeline orchestration using Execute Pipeline and Tumbling Window Triggers.

This project is a practical showcase of how modern cloud data engineering principles can be applied using Microsoft Azure services for scalable, modular, and reusable data processing solutions.

## 📊 Project Technical Architecture Diagram

![ADF Architecture](Azure%20End-to-End%20ADF%20Project%20Architecture.png)

#### 1. Source Layer

- ECDC Website (API): Supplies daily COVID-19 statistics like cases, deaths, hospital admissions, and testing data.
- Azure Blob Storage: Stores static reference files such as population datasets.

#### 2. Extract Layer

Azure Data Factory (ADF) pipelines are used to extract data from:
- ECDC API (HTTP linked service)
- Azure Blob Storage (Blob linked service)
Raw data is stored in the Raw zone of Azure Data Lake Gen2.

#### 3. Transform Layer

ADF Mapping Data Flows and Azure Databricks notebooks are used to:

- Cleanse and reshape data
- Pivot and split metrics
- Perform aggregations and enrich data with country/date dimensions
- Processed data is stored in the Processed zone of Azure Data Lake Gen2.

#### 4. Load Layer

- Transformed data is copied into an Azure SQL Database using ADF pipelines.
- This includes fact and dimension tables needed for reporting.

#### 5. Analytics Layer

- Power BI connects to Azure SQL DB for interactive dashboards and data visualizations.
- Optional: Machine Learning workloads can leverage curated data stored in Data Lake or SQL for model training and predictions.

## 📤 Data Transfer Diagram

The solution follows a layered architecture:

- **Extract Layer:** Fetches raw data from APIs and Blob storage
- **Transform Layer:** Cleans and reshapes data via ADF Data Flows and Databricks
- **Load Layer:** Pushes processed data into Azure SQL Database
- **Analytics Layer:** Visualizes the data in Power BI and supports ML tasks

![Data Transfer Diagram](Azure%20End-to-End%20Data%20Transfer%20Diagram.png)

## 🏗️ Components

### ADF Pipelines
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
