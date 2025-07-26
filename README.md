# 🚖 NYC Taxi Analytics Platform
🔍 Overview
This project is a real-world batch data pipeline built using Databricks, PySpark, Delta Lake, and databricks dashboard, simulating how modern tech companies ingest, process, and analyze high-volume datasets.

We use NYC Taxi trip data to build a complete ETL pipeline from ingestion to gold-level analytics and dashboards. The goal is to show how data engineers can create scalable, production-ready pipelines with validation, orchestration, and business-focused insights.

🎯 Business Objective
The aim is to enable:

Taxi fleet managers to identify high-revenue zones and optimize dispatch

City planners to monitor congestion and plan infrastructure

Finance teams to analyze monthly revenue, payment trends, and fare breakdowns

Data teams to run automated, traceable, and incremental data pipelines

🧱 Architecture
The project follows a classic Medallion Architecture:

Raw Data (.parquet)
    ↓
[ Bronze Layer ]
    • Reads raw NYC Taxi trip data
    • Adds metadata (file name, ingestion time)
    • Stores as Delta Lake table
    ↓
[ Silver Layer ]
    • Cleans nulls, filters bad rows
    • Adds surrogate keys
    • Validates schema
    ↓
[ Gold Layer ]
    • Joins with dimension tables (e.g. zone lookup)
    • Computes aggregations: revenue, traffic patterns
    • Builds fact and dimension marts
    ↓
Dashboards
    • Revenue trends
    • Pickup/drop-off heatmaps
    • Payment method analysis
    
⚙️ Tools & Technologies
Tool	Purpose
Databricks	Unified platform for PySpark execution
Delta Lake	ACID-compliant data lake
GCS	Cloud storage (optional for raw files)
PySpark	Scalable distributed processing
Databricks for Interactive dashboards for insights

🪜 ETL Pipeline Breakdown
1️⃣ Raw → Bronze
Reads NYC Green Taxi data in .parquet format

Adds metadata columns: source filename, ingestion timestamp

Stores raw data as Delta table

2️⃣ Bronze → Silver
Filters nulls, drops irrelevant records

Adds surrogate keys for primary indexing

Ensures idempotency by checking previously processed files

Validates schema

3️⃣ Silver → Gold
Joins with dimension tables (e.g., zones, time)

Computes:

Revenue per borough

Busiest zones by pickup/dropoff

Payment type distributions

Stores as fact & dimensional marts

📊 Dashboards
Built using Power BI on top of the Gold Layer:

Monthly Revenue Report

Borough-to-Borough Traffic Heatmap

Payment Type Breakdown

Top 10 Pickup/Drop Zones

These dashboards simulate executive-level reporting and can be refreshed daily using batch scheduling.

✅ Features
✅ Incremental ingestion (no duplicate processing)

✅ Data validation & schema enforcement

✅ Surrogate key generation for warehouse compatibility

✅ Bronze–Silver–Gold medallion architecture

✅ Built for cloud or local Databricks environments

✅ Real-world dashboards aligned to business KPIs

📌 How to Run
Launch Databricks Community or Free Edition

Upload and run notebooks in order:

bronze_ingestion.ipynb

silver_cleaning.ipynb

gold_modelling.ipynb

Connect to Databricks SQL endpoint or export CSVs

Open dashboards to visualize metrics

📈 Sample Use Cases
Use Case	Description
Fleet optimization	Identify high-volume boroughs to prioritize cabs
Dynamic pricing	Analyze peak hours by pickup datetime
Fraud detection	Flag abnormally short trips or negative fares
Revenue reporting	Track total fares and tip amounts over time

🧠 What I Learned
Building scalable, modular pipelines using PySpark

Working with real-world messy datasets

Ensuring data quality and idempotency

Building business-useful dashboards

Simulating production-grade practices in the cloud
