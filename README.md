# Azure End-to-End Data Engineering: Olympic Data Analytics

## 📌 Project Overview
This project implements a full-scale data engineering pipeline on **Microsoft Azure** to analyze the Tokyo Olympic dataset.The pipeline handles data ingestion, storage, transformation, and advanced analytics using a modern tech stack including **Azure Data Factory**, **Azure Databricks**, and **Synapse Analytics**[cite: 3465, 3467].

## 🏗️ System Architecture
[cite_start]The data flow follows a "Lakehouse" architecture pattern[cite: 3467]:
1.  **Data Source:** Raw Olympic data (CSVs).
2.  **Ingestion:** **Azure Data Factory (ADF)** orchestrates the movement of data.
3.  [cite_start]**Storage:** **Azure Data Lake Gen2 (ADLS)** stores both `raw-data` and `transformed-data` in separate containers[cite: 3543].
4.  [cite_start]**Transformation:** **Azure Databricks** mounts the Data Lake, processes the data using PySpark, and performs exploratory data analysis (EDA)[cite: 3622].
5.  [cite_start]**Analytics & Serving:** **Azure Synapse Analytics** runs SQL queries on the processed data for final reporting[cite: 3470].

## 📂 Dataset
[cite_start]The dataset consists of five CSV files stored in the `raw-data` container[cite: 3556]:
* `Athletes.csv`
* `Coaches.csv`
* `EntriesGender.csv`
* `Medals.csv`
* `Teams.csv`

## 🛠️ Tech Stack
* **Cloud Provider:** Microsoft Azure
* [cite_start]**ETL Orchestration:** Azure Data Factory (V2) [cite: 3523]
* [cite_start]**Storage:** Azure Data Lake Storage Gen2 [cite: 3469]
* [cite_start]**Processing:** Azure Databricks (Spark/Python) [cite: 3508]
* [cite_start]**Warehousing/SQL:** Azure Synapse Analytics [cite: 3518]

## 🧠 Data Transformation & Analysis (Databricks)
We utilized **PySpark** and **Pandas** within Databricks to clean and visualize the data. Key insights generated include:

### 1. Gold Medal Analysis
* Aggregated medals by country to identify top performers.
* [cite_start]**Top Countries:** USA, China, Japan, Great Britain, and ROC[cite: 3673, 3681].
* [cite_start]**Visualization:** A pie chart displaying the share of gold medals among the top nations[cite: 3778].

### 2. Gender Distribution
* Analyzed the `EntriesGender` dataset to calculate the average number of male vs. female entries per discipline.
* [cite_start]**Key Finding:** The overall gender distribution is nearly balanced, with **48% Female** and **52% Male** participation[cite: 3828, 3830].
* [cite_start]**Visualization:** Stacked bar charts and pie charts representing gender parity across disciplines[cite: 3703].

## 📊 Synapse Analytics (SQL)
Final data querying was performed in Synapse Studio using serverless SQL pools.
* **Sample Query:** Grouping athletes by discipline to count participation.
    ```sql
    SELECT Discipline, COUNT(*) AS AthleteCount
    FROM athletes
    GROUP BY Discipline;
    ```
    [cite_start][cite: 3848]
* [cite_start]**Visuals:** Generated line charts to visualize athlete and coach counts per discipline directly within Synapse[cite: 3887].

## 🚀 How to Run
1.  [cite_start]**Setup Azure Resources:** Create a Resource Group (`Olympic`) containing ADF, Databricks, ADLS Gen2, and Synapse[cite: 3471].
2.  **Ingest Data:** Use ADF to copy the CSV files into the `raw-data` container.
3.  [cite_start]**Mount Storage:** Run the provided Databricks notebook to mount ADLS using OAuth credentials[cite: 3622].
4.  **Execute Notebooks:** Run the Spark jobs to transform data and generate visualizations.
5.  **Query:** Connect Synapse to the `transformed-data` container and run SQL scripts.

## 👤 Author
[cite_start]Tanishq Shinde [cite: 3475]
