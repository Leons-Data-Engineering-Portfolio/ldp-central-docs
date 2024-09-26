## Techstack:
- Data Sources:
  - API's
  - CSV files
-  Orchestration:
    - Apache Airflow
- Data Storage:
   - Data Warehouse (PostgreSQL):
     - RAW_DATA: Unprocessed raw data (structured)
     - SUMMARY_DATA: Cleaned and transformed data
 - Data Visualization:
   - Apache Superset
- Containerization:
  - Docker for deploying the different components

## Pipeline Overview

### 1. Data Extraction

- Use **Apache Airflow** to define DAGs (Directed Acyclic Graphs) that use defined pyhton ETL code to extract data from various sources (APIs, databases, etc.)

### 2. Loading Raw Data

- Load structured data into PostgreSQL without performing any transformations at this stage.
- The Airflow tasks will handle the loading process by using defined pyhton ETL code.

### 3. Transformations in PostgreSQL

- After loading the raw data, use SQL within PostgreSQL to perform necessary transformations:
  - Data cleaning (removing duplicates, handling missing values).
  - Aggregation and summarization.
  - Joining data from different tables to create a consolidated view.
- The transformations are orchestrated by Airflow.

### 4. Data Visualization

- Use a BI tool like **Apache Superset** to create dashboards and visualizations based on the transformed data stored in the `SUMMARIZE_DATA` schema.
- Connect Superset to PostgreSQL to directly query the transformed data for visualization.
