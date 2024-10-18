# e-Game Cricket 22 Stats Tracking Project

## Project Overview

This project tracks and analyzes game statistics from **e-Game Cricket 22**, covering **batting**, **bowling**, and **tournaments won** by the respective teams of three friends over the course of one year. Data is manually entered into Excel sheets and processed using various Azure-based tools for transformation and analysis.

## Project Workflow

1. **Data Entry**:
   - Game stats, including batting, bowling, and tournament wins, are manually entered into Excel sheets.

2. **Upload to Azure Data Lake Storage (ADLS)**:
   - Excel sheets are uploaded from the local system to **Azure Data Lake Storage (ADLS)**, where they are stored as raw data (Bronze layer).

3. **Data Cleaning and Transformation in Databricks**:
   - Data is cleaned and transformed using **Azure Databricks**.
   - The project follows the **Medallion Architecture**:
     - **Bronze Layer**: Raw, unprocessed data.
     - **Silver Layer**: Cleaned and transformed data.
     - **Gold Layer**: Aggregated, analytics-ready data.

4. **ADF Pipeline**:
   - An **Azure Data Factory (ADF) pipeline** is used to orchestrate and run the Databricks notebook.
   - A trigger monitors the Bronze layer in ADLS for new uploads and initiates data processing.

5. **Azure Synapse Analytics**:
   - The **Synapse pipeline** executes a stored procedure to generate views in the **Synapse Data Warehouse** (serverless).
   - These views are based on the fully processed data from the Gold layer.

6. **Power BI Dashboards**:
   - **Power BI** connects to Azure Synapse to visualize statistics for each team.
   - Key metrics include batting and bowling performance and tournament wins.

## Architecture

- **Azure Data Lake Storage (ADLS)**:
  - **Bronze Layer**: Raw Excel files.
  - **Silver Layer**: Cleaned data.
  - **Gold Layer**: Final, analytics-ready data.
  
- **Azure Databricks**:
  - Used for data processing and transformations.
  - Follows the Medallion Architecture for structured data flow.

- **Azure Data Factory (ADF)**:
  - Automates the data processing pipeline.
  - Triggers Databricks notebooks when new data is uploaded.

- **Azure Synapse Analytics**:
  - Provides serverless data warehousing.
  - Executes stored procedures to generate views of the Gold-layer data.

- **Power BI**:
  - Connects to Synapse for creating visualizations of the processed data.

## Setup Instructions

1. **Upload Excel Files**:
   - Upload manually entered game stats in Excel format to the Bronze layer in ADLS.

2. **Trigger Data Pipeline**:
   - The ADF pipeline triggers automatically upon new file uploads to the Bronze layer.

3. **Data Processing**:
   - Databricks cleans and transforms the data from the Bronze layer to Silver and then to the Gold layer.

4. **Synapse Views**:
   - The Synapse pipeline creates views for the processed data.

5. **Power BI**:
   - Connect Power BI to Synapse to create dashboards for visualizing game stats.

## Technologies Used

- **Azure Data Lake Storage (ADLS)**
- **Azure Databricks**
- **Azure Data Factory (ADF)**
- **Azure Synapse Analytics**
- **Power BI**

