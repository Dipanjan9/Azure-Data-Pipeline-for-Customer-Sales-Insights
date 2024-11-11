# Azure-Data-Pipeline-for-Customer-Sales-Insights

Azure Data Pipeline for Customer & Sales Insights

This project implements a data pipeline to generate actionable insights from customer and sales data, leveraging Azure services for data ingestion, transformation, and visualization. Stakeholders can use an interactive Power BI dashboard to analyze key metrics like Sales by Gender and Product Category, with options to filter by date, product category, and gender.

Table of Contents
Overview
Business Requirements
Solution Architecture
Technology Stack
Setup Instructions
Pipeline Components
Security and Governance
Testing
Contributing
License
Overview
This project addresses a business need to understand customer demographics and their impact on sales. By building an end-to-end data pipeline, it enables stakeholders to access current and actionable insights into gender distribution and product purchases through an interactive dashboard.

Business Requirements
Sales by Gender and Product Category: A dashboard visualizing total products sold, total sales revenue, and a gender distribution among customers.
Data Filtering: Ability to filter data by product category, gender, and date.
User-Friendly Interface: Stakeholders should access an easy-to-use, interactive dashboard for exploring insights.
Solution Architecture
The solution comprises several components, organized into data ingestion, transformation, loading, and reporting layers. Here’s a high-level flow:

Data Ingestion:

Extracts customer and sales data from an on-premises SQL database.
Loads data into Azure Data Lake Storage (ADLS) using Azure Data Factory (ADF).
Data Transformation:

Cleans and transforms the data in Azure Databricks.
Structures data into Bronze (raw), Silver (cleansed), and Gold (aggregated) layers.
Data Loading and Reporting:

Loads aggregated data into Azure Synapse Analytics for analysis.
Builds a Power BI dashboard for visualizing insights.
Automation:

Automates the pipeline to run daily, ensuring data and reports are always up-to-date.

Technology Stack
Azure Data Factory (ADF): Orchestrates data movement and transformation.
Azure Data Lake Storage (ADLS): Stores raw and processed data.
Azure Databricks: Processes and transforms data.
Azure Synapse Analytics: Data warehousing and SQL-based analytics.
Power BI: Visualization and reporting.
Azure Key Vault: Manages credentials and secrets securely.
SQL Server (On-Premises): Source of customer and sales data.
Setup Instructions
Prerequisites
Azure account with sufficient credits.
Access to an on-premises SQL Server database.
Steps
Azure Environment Setup

Create a new resource group.
Provision services:
Azure Data Factory (ADF)
Azure Data Lake Storage (ADLS) with bronze, silver, and gold containers.
Azure Databricks and Synapse Analytics workspaces.
Azure Key Vault for secret management.
Data Ingestion

Set up SQL Server: Install SQL Server and SQL Server Management Studio (SSMS).
Restore the AdventureWorks database.
Create ADF pipelines to copy data from SQL Server to the bronze layer in ADLS.
Data Transformation

Mount ADLS in Databricks.
Use Databricks notebooks to clean and aggregate data, transitioning it from bronze to silver to gold layers.
Data Loading and Reporting

Set up a Synapse SQL pool and load the gold data for analysis.
Connect Power BI to Synapse and create visualizations per business requirements.
Automation and Monitoring

Use ADF to schedule data pipelines for daily runs.
Monitor pipeline execution with ADF and Synapse’s monitoring tools.
Security and Governance

Manage access with role-based access control (RBAC) using Azure Entra ID (formerly Active Directory).
Pipeline Components
Data Quality Checks: Automated checks for data consistency at each stage.
Logging and Error Handling: Detailed logging and error-handling mechanisms to monitor pipeline performance.
Incremental Data Loads: Incremental loading to optimize resources.
Power BI Dashboard: An interactive dashboard with the following key metrics:
Total products sold by gender and category.
Total sales revenue by gender and category.
Filters by date, product category, and gender.
Security and Governance
Data Encryption: Ensure data encryption in transit and at rest within ADLS and Synapse.
Sensitive Data Handling: Mask or anonymize sensitive customer data.
Access Control: Set up RBAC using Azure Entra ID for secure access management.
Testing
End-to-End Pipeline Testing:

Insert new records into the on-premises SQL database.
Trigger the pipeline to verify data flows through all components.
Confirm that the Power BI dashboard updates with new data.
Load and Performance Testing:

Test performance under expected load to ensure dashboard responsiveness.
Contributing
Contributions are welcome! Please fork this repository and submit a pull request with a description of your changes.

License
MIT License
