# Azure End-to-End Data Engineering: Olympic Data Analytics

## 📌 Project Overview
This project implements a full-scale data engineering pipeline on **Microsoft Azure** to analyze the Tokyo Olympic dataset.The pipeline handles data ingestion, storage, transformation, and advanced analytics using a modern tech stack including **Azure Data Factory**, **Azure Databricks**, and **Synapse Analytics** .

## 🏗️ System Architecture
The data flow follows a "Lakehouse" architecture pattern:
1.  **Data Source:** Raw Olympic data (CSVs).
2.  **Ingestion:** **Azure Data Factory (ADF)** orchestrates the movement of data.
3.  **Storage:** **Azure Data Lake Gen2 (ADLS)** stores both `raw-data` and `transformed-data` in separate containers.
4.  **Transformation:** **Azure Databricks** mounts the Data Lake, processes the data using PySpark, and performs exploratory data analysis (EDA).
5.  **Analytics & Serving:** **Azure Synapse Analytics** runs SQL queries on the processed data for final reporting.

## 📂 Dataset
The dataset consists of five CSV files stored in the `raw-data` container:
* `Athletes.csv`
* `Coaches.csv`
* `EntriesGender.csv`
* `Medals.csv`
* `Teams.csv`

## 🛠️ Tech Stack
* **Cloud Provider:** Microsoft Azure
* **ETL Orchestration:** Azure Data Factory (V2) 
* **Storage:** Azure Data Lake Storage Gen2 
* **Processing:** Azure Databricks (Spark/Python) 
* **Warehousing/SQL:** Azure Synapse Analytics 

## 🧠 Data Transformation & Analysis (Databricks)
We utilized **PySpark** and **Pandas** within Databricks to clean and visualize the data. Key insights generated include:

### 1. Gold Medal Analysis
* Aggregated medals by country to identify top performers.
* **Top Countries:** USA, China, Japan, Great Britain, and ROC.
* **Visualization:** A pie chart displaying the share of gold medals among the top nations.

### 2. Gender Distribution
* Analyzed the `EntriesGender` dataset to calculate the average number of male vs. female entries per discipline.
* **Key Finding:** The overall gender distribution is nearly balanced, with **48% Female** and **52% Male** participation.
* **Visualization:** Stacked bar charts and pie charts representing gender parity across disciplines.

## 📊 Synapse Analytics (SQL)
Final data querying was performed in Synapse Studio using serverless SQL pools.
* **Sample Query:** Grouping athletes by discipline to count participation.
    ```sql
    SELECT Discipline, COUNT(*) AS AthleteCount
    FROM athletes
    GROUP BY Discipline;
    ```
    
* **Visuals:** Generated line charts to visualize athlete and coach counts per discipline directly within Synapse.

## 🚀 How to Run
1.  **Setup Azure Resources:** Create a Resource Group (`Olympic`) containing ADF, Databricks, ADLS Gen2, and Synapse.
2.  **Ingest Data:** Use ADF to copy the CSV files into the `raw-data` container.
3.  **Mount Storage:** Run the provided Databricks notebook to mount ADLS using OAuth credentials.
4.  **Execute Notebooks:** Run the Spark jobs to transform data and generate visualizations.
5.  **Query:** Connect Synapse to the `transformed-data` container and run SQL scripts.

## 👤 Author
Tanishk Nanasaheb Shinde
