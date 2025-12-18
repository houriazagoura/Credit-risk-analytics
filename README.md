# Credit-risk-analytics
End-to-end credit risk analytics project: data generation, cleaning, modeling and interactive PowerBI dashboards.

## Project Overview 
This project presents an end-to-end credit risk analytics workflow built on a synthetically generated retail loan portfolio.
It covers the full data lifecycle, from data generation and modeling to data integration, quality validation, and preparation for analytics and visualization.

The project follows a structured data architecture using Azure Databricks and a dimensional data model to ensure clarity, scalability, and analytical efficiency. 
The resulting dataset is designed to support portfolio analysis, credit risk modeling, and interactive dashboards, while respecting data security and confidentiality constraints.

## Data generation 
The dataset used in this project is synthetically generated to simulate a retail credit portfolio.
Loan-level records are created using statistical distributions and rule-based assumptions to reflect realistic lending characteristics, including borrower segmentation, product definitions, exposure amounts, and default behavior.
The generation process is designed to preserve coherence between borrower profiles and credit risk dynamics, while avoiding the use of any real or sensitive data.
## Data Processing Approach 
Data is processed using Azure Databricks following a Bronze–Silver–Gold architecture based on Delta tables.
## Data Description

The dataset is organized around a simple and consistent data model designed for credit risk analytics.

### Core Tables

- **DIM_PRODUCT**  
  Contains descriptive information about loan products, such as product categories and types.  
  This dimension supports segmentation and comparative analysis across different credit products.

- **DIM_CUSTOMER**  
  Stores borrower-related attributes and segmentation variables (e.g. income bucket, credit score bucket).  
  It enables customer-level risk profiling and portfolio segmentation.

### Fact Tables

- **FACT_LOAN**  
  The main fact table of the model, with one record per loan.  
  It includes core loan attributes, exposure amounts, origination information, and default indicators.  
  The structure is intentionally kept simple to support analytics and modeling.

- **FACT_CASHFLOW (theoretical)**  
  Represents theoretical loan cash flows derived from loan characteristics.  
  This table is designed to support future extensions such as loss modeling or scenario analysis.

All tables are synthetically generated and independent of any external data source.  
The data model is designed to support data quality analysis, risk modeling, and dashboarding in a clear and scalable way.

## Data Integration & Granularity

The data model follows a loan-level granularity, where each record in the main fact table represents a single loan.

Dimension tables (DIM_PRODUCT, DIM_CUSTOMER) are joined to the loan fact table using stable surrogate keys to enrich loan records with descriptive attributes.
Theoretical cash flow data is linked at the loan level and derived from loan characteristics.

Data is ingested into the Bronze layer, while transformations and joins are performed in the Silver layer using Delta tables.
The Gold layer exposes clean, analytics-ready tables designed for direct consumption in Power BI.
