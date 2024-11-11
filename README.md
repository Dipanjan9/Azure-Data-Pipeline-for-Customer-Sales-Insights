# Azure Data Engineering Pipeline for Customer & Sales Insights

This project builds an end-to-end Azure Data Engineering solution. The pipeline performs **Data Ingestion**, **ETL (Extract, Transform, Load)**, and **Analytics**, all using Microsoft Azure services and Power BI for visualization.

## Goal of the Project

The project aims to create an Azure-based solution to migrate data from an on-premises SQL Server database to the cloud. It leverages **Azure Data Factory** for data ingestion, **Azure Databricks** for data transformation, and **Azure Synapse Analytics** for warehousing and analytics. The final output is an interactive **Power BI dashboard** that stakeholders can use to explore insights into customer demographics and product sales.

Data migration to the cloud is a common scenario for data engineers working with organizations of all sizes. This project has allowed me to gain hands-on experience with key data engineering skills, including:

* Data Ingestion and ETL
* Cloud Data Transformation using Azure Databricks
* Analytics and Dashboard Reporting with Power BI
* Data Security and Governance in Azure

![Solution Architecture Diagram](https://your-image-link-here)

## Prerequisites

1. **Microsoft SQL Server Management Studio (SSMS)** installed on-premises.
2. **Azure Subscription** with the following services:
   * Azure Data Lake Storage Gen2
   * Azure Data Factory
   * Azure Key Vault
   * Azure Databricks
   * Azure Synapse Analytics
   * Microsoft Entra ID for access control
3. **Microsoft Power BI**
4. **AdventureWorksLT2022** database set up with user credentials 'usr1', with the same credentials stored as secrets in Azure Key Vault.

The database used for this project is **AdventureWorksLT2022**, a sample sales database.

## Implementation

### Part 1: Data Ingestion

1. **Restore AdventureWorksLT2022 Database**: Set up the AdventureWorks database in SQL Server.
   ![Database Setup](https://your-image-link-here)

2. **Azure Integration Runtime**: Set up an integration runtime in ADF to bridge between on-premises SQL Server and Azure.
3. **Data Copy Pipeline**: Create a pipeline in ADF to copy data from the SQL Server to the **bronze layer** in Azure Data Lake Storage Gen2. Data is stored in **Parquet format**.

![Bronze Layer](https://your-image-link-here)

### Part 2: Data Transformation

Data transformation is carried out in **Azure Databricks** with PySpark. The transformation includes two stages:

1. **Bronze to Silver Transformation**: Clean and pre-process the raw data.
2. **Silver to Gold Transformation**: Standardize and aggregate data for business reporting.

Final data in the **gold layer** is stored in **Delta format**, ready for analytics and reporting.

![Data Transformation Process](https://your-image-link-here)

These transformation notebooks are automated in the ADF pipeline, creating a seamless data flow from ingestion to transformation.

![ADF Pipeline Integration](https://your-image-link-here)

### Part 3: Data Loading

1. **Load Data into Synapse Analytics**: Set up Azure Synapse Analytics to load the transformed data from the gold layer.
2. **Stored Procedure Execution**: Use stored procedures in Synapse to create and update views in Azure SQL Database for reporting.

![Synapse Loading](https://your-image-link-here)

### Part 4: Data Reporting

Connect **Power BI** to the Azure Synapse data views and create an interactive dashboard with key insights on:

* Sales distribution by gender and product category.
* Total products sold and revenue by category.

![Power BI Dashboard](https://your-image-link-here)

### Part 5: Automation and Monitoring

1. **Daily Scheduled Triggers**: Configure ADF to run the pipeline daily, ensuring data is up-to-date in Power BI.
2. **Monitoring**: Use ADF’s monitoring features to oversee pipeline executions and manage any errors or alerts.

![Pipeline Monitoring](https://your-image-link-here)

By automating the entire data pipeline, the project provides stakeholders with continuously updated insights.

## End Notes

* This project demonstrates how to set up a scalable data pipeline using Azure services such as ADF, Databricks, and Synapse.
* Access management is secured using **role-based access control (RBAC)** via **Microsoft Entra ID**.
* While the AdventureWorks database is relatively small, the solution architecture is designed to be adaptable for larger datasets and more complex pipelines.
* Using Azure Databricks and Synapse enhances data transformation and analytics capabilities beyond what could be achieved with ADF alone, providing greater flexibility and processing power.
