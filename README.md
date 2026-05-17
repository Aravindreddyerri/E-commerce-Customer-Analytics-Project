# E-commerce Customer Analytics with Microsoft Fabric

## Overview
This project builds an end-to-end analytics pipeline in Microsoft Fabric using e-commerce CSV data stored in ADLS Gen2. The solution ingests raw files into a Lakehouse, transforms them with PySpark in a Fabric notebook, creates a gold customer analytics table, and visualizes the results in Power BI.

## Project Goal
The goal of the project is to turn raw customer and transaction data into a clean analytics model for reporting and business insights. The final output supports customer behavior analysis using integrated order, payment, support, and web activity data.

## Dataset
The project uses the following CSV files:

- `customers.csv`
- `orders.csv`
- `payments.csv`
- `support_tickets.csv`
- `web_activities.csv`

## Architecture
The implementation follows a bronze-silver-gold architecture in Microsoft Fabric.

- **Bronze layer:** Raw data copied from ADLS Gen2 into the Fabric Lakehouse.
- **Silver layer:** Cleaned and standardized tables created in a Fabric notebook using PySpark.
- **Gold layer:** Unified customer analytics table created by joining all cleaned datasets.
- **Reporting layer:** Power BI dashboard built for customer analysis.

## Pipeline Flow
The Fabric pipeline uses a metadata activity, a ForEach loop, a copy activity, and a notebook activity. The pipeline first identifies source files, copies them into the Lakehouse, and then triggers the notebook for transformation logic.

<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/92545080-e608-4406-8a56-a51a48dea822" />


## ADF-Style Pipeline
The ingestion workflow was implemented with a Microsoft Fabric Data Pipeline that follows an Azure Data Factory style orchestration pattern. It uses a `Get Metadata` activity to read available files, a `ForEach` activity to iterate through them, a `Copy Data` activity to load them into the Lakehouse bronze layer, and a notebook activity to run PySpark transformations.

### Screenshot Notes
Add screenshots for the pipeline canvas, the ForEach copy activity, and the successful run output in this section of the repository documentation.

## Transformations
The Fabric notebook performs the following transformations:

- Standardizes names, emails, gender values, and location fields in customer data.
- Converts inconsistent date formats into proper date columns across orders, payments, support, and web activity datasets.
- Casts numeric fields such as amount into proper numeric types and removes invalid negative values.
- Removes duplicate rows and drops records with missing critical fields.
- Normalizes text values such as status, issue type, page viewed, payment method, and device type.

## Gold Table
The final table, `goldcustomer360`, combines customer profile data with orders, payments, support tickets, and web activities. It provides a single source for reporting and dashboard creation.

## Power BI Dashboard
The Power BI report contains visuals for:

- Order amount by location.
- Order amount by payment method.
- Order amount by gender.
- Ticket count by ticket ID.
- Order amount by date.
- Order amount by device type.

The dashboard indicates that Surat leads in total order amount, male customers contribute the largest share of orders, and Android is the most represented device type in the report snapshot.
<img width="2880" height="1800" alt="image" src="https://github.com/user-attachments/assets/c070c13f-f153-453c-9a12-f527e751199b" />


## Tech Stack
- Azure Data Lake Storage Gen2
- Microsoft Fabric Data Pipeline
- Microsoft Fabric Lakehouse
- Fabric Notebook (PySpark)
- Delta Tables
- Power BI

## Key Learnings
- Built an end-to-end data pipeline in Microsoft Fabric.
- Applied medallion architecture using bronze, silver, and gold layers.
- Performed data cleaning and transformation using PySpark.
- Created a business-facing Power BI dashboard from curated data.

## Project Outcome
This project demonstrates practical data engineering and analytics skills using Microsoft Fabric. It shows how raw cloud-based datasets can be transformed into a curated reporting model for customer analysis.
