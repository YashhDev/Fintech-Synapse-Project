# 📊 Fintech CDC Data Migration Pipeline

![Fintech CDC Pipeline Overview](docs/architecture.png)


---

This project implements a **Change Data Capture (CDC) data migration pipeline** for a FinTech domain using **Azure Synapse Analytics** and **Azure Data Lake Storage (ADLS)**.  
It automates the ingestion of multiple SQL database tables into **Bronze**, **Silver**, and **Gold** layers, enabling efficient financial data processing and analytics.

---

## 📌 Table of Contents
1. [Overview](#overview)
2. [Architecture](#architecture)
3. [Tech Stack](#tech-stack)
4. [Data Flow](#data-flow)
5. [Folder Structure](#folder-structure)
6. [Setup Instructions](#setup-instructions)
7. [Sample Output](#sample-output)
8. [Future Enhancements](#future-enhancements)
9. [License](#license)

---

## 📜 Overview
The **Fintech CDC Data Migration Pipeline**:
- Extracts data from a **SQL database** (e.g., `Customers`, `Accounts`, `Loans`, `Payments`, `Transactions`).
- Loads it into **ADLS** in Bronze layer.
- Validates and promotes data to **Silver** and **Gold** layers.
- Designed for **incremental data loads** and optimized for large datasets.

---

## 🏗 Architecture

![Fintech CDC Pipeline Overview](docs/architecture.png)

**Process:**
1. **SQL Database** – Source tables for Customers, Accounts, Loans, Payments, Transactions.
2. **Synapse Pipelines**:
   - **Lookup**: Retrieves list of tables to process.
   - **For Each**: Loops through tables.
   - **Copy Activity**: Loads data into **Bronze** layer.
   - **Validation & Promotion**: Moves data to **Silver** (on success) or logs errors.
3. **ADLS**:
   - Organized into Bronze, Silver, Gold zones for raw, cleansed, and curated data.

---

## 🛠 Tech Stack
- **Azure Synapse Analytics** – Orchestration & transformations.
- **Azure Data Lake Storage Gen2** – Data storage (Bronze, Silver, Gold).
- **SQL Database** – Source data.
- **Parquet** – File format for optimized analytics.
- **CDC** – Incremental data ingestion.

---

## 🔄 Data Flow
1. **Ingestion**:
   - Synapse `Lookup` fetches table names.
   - For each table, Synapse `Copy Activity` loads data into `Bronze`.
2. **Processing**:
   - On successful copy, data is validated and promoted to `Silver`.
   - Enriched/curated data is stored in `Gold`.
3. **Consumption**:
   - Analysts and BI tools connect to Silver/Gold layers for reporting.

---

## 📂 Folder Structure


---

## ⚡ Setup Instructions
1. **Clone the repository**
   ```bash
   git clone https://github.com/YashhDev/Fintech-Synapse-Project.git
   cd Fintech-Synapse-Project
2 Provision Azure Resources
2.1 Create an Azure Synapse Workspace.
2.2 Create an Azure Data Lake Storage Gen2 (ADLS Gen2) account.
2.3 Create a SQL Database to hold your source data.

3 Upload Sample Data
3.1 Place CSV files into your source database tables or connect Synapse to your existing SQL database.

4 Import Pipelines
4.1 Open Synapse Studio.
4.2 Import the pipeline JSON file from the pipelines/ folder in this repo.

5 Run Pipeline
5.1 In Synapse Studio, trigger the pipeline run.
5.2 Monitor execution to ensure all steps complete successfully.

