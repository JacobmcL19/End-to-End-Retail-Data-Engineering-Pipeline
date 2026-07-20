# End-to-End Retail Data Engineering Pipeline

An end-to-end analytics engineering project built around a fully synthetic retail dataset. The notebook simulates a complete retail data workflow: raw data generation, validation, cleaning, feature engineering, dimensional modeling, DuckDB warehousing, SQL analytics, KPI generation, dashboarding, and automated reporting.

## Overview

The notebook demonstrates a modern retail data pipeline that moves data through the following stages:

Raw Data -> Validation -> Cleaning -> Feature Engineering -> Star Schema -> DuckDB Warehouse -> SQL Analytics -> Business KPIs -> Interactive Dashboard -> Data Quality Report -> Executive Summary

It generates a realistic retail operating environment with:

- 10,000 customers
- 1,000 products
- 50 stores
- 100,000 orders

## Technologies

The notebook uses:

- Python
- Pandas
- NumPy
- Faker
- DuckDB
- Plotly
- PyArrow
- ReportLab

## What The Notebook Does

The pipeline creates synthetic retail source data, profiles it for quality issues, cleans and standardizes the datasets, and builds a warehouse-ready dimensional model. It then loads the data into DuckDB, runs SQL analytics, calculates business KPIs, creates an executive dashboard, and exports reporting artifacts for stakeholders.

### 1. Synthetic Data Generation

The notebook builds retail-style source tables for customers, products, stores, orders, returns, and dates. It also defines business assumptions such as:

- Regions
- Payment methods
- Order statuses
- Shipping methods
- Customer segments
- Product catalog categories

### 2. Data Profiling And Validation

Before transformation, the notebook profiles each dataset and checks for:

- Row counts
- Column counts
- Data types
- Missing values
- Duplicate records
- Unique values
- Memory usage
- Outliers
- Invalid business rules

The validation layer focuses on issues such as:

- Duplicate orders
- Missing customer IDs
- Missing sales values
- Negative or impossible quantities
- Future dates
- Profit outliers

### 3. Data Cleaning Pipeline

The notebook standardizes data types, resolves quality issues, and records the actions in a cleaning audit log. The cleaned outputs are written to the `data/cleaned/` folder.

### 4. Feature Engineering And Dimensional Modeling

The cleaned operational tables are converted into warehouse-ready structures, including:

- `dim_customer`
- `dim_product`
- `dim_store`
- `dim_date`
- `fact_sales`

The notebook also computes customer and product features used for business analysis, including RFM-style metrics, customer lifetime value, purchase frequency, repeat rates, margin analysis, and segment-level summaries.

### 5. DuckDB Warehouse

The notebook creates a DuckDB warehouse and exports both CSV warehouse tables and the DuckDB database itself. The warehouse artifacts are written to `data/warehouse/`.

### 6. Advanced SQL Analytics

The warehouse is queried with SQL to produce operational and executive insights, including revenue, profit, customer segmentation, product performance, store performance, and category-level ranking analysis.

### 7. KPI Engine

The notebook compiles executive KPIs such as:

- Total revenue
- Total profit
- Total units sold
- Average order value
- Repeat customer rate
- Average customer lifetime value
- Return rate
- Top category
- Highest margin category

### 8. Interactive Executive Dashboard

The project includes a Plotly-based dashboard for visual exploration of the retail business, with charts built from the warehouse and KPI outputs.

### 9. Automated Reporting

The notebook exports reporting outputs into the `reports/` folder, including:

- `dataset_profile.csv`
- `missing_values.csv`
- `duplicates.csv`
- `data_types.csv`
- `validation_summary.csv`
- `cleaning_audit.csv`
- `recommendations.csv`
- `data_quality_report.csv`
- `business_metrics.csv`
- `executive_kpi_report.csv`

## Repository Structure

```text
README.md
Sales_Data_Pipeline.ipynb
Archtecture/
	Architecture.txt
data/
	raw/
	cleaned/
	warehouse/
reports/
```

## Generated Artifacts

### Raw Data

The notebook creates synthetic source files in `data/raw/`.

### Cleaned Data

The cleaned, validated datasets are written to `data/cleaned/`.

### Warehouse

The star-schema outputs and DuckDB database are stored in `data/warehouse/`.

### Reports

Quality, profiling, KPI, and recommendation outputs are stored in `reports/`.

## How To Run

1. Open `Sales_Data_Pipeline.ipynb` in VS Code or Jupyter.
2. Install the required Python packages if they are not already available.
3. Run the notebook from top to bottom.
4. Review the generated files in `data/` and `reports/`.

## Notes

- The dataset is synthetic and generated entirely within the notebook.
- The pipeline is deterministic because the notebook sets a fixed random seed.
- The notebook is designed to be rerunnable and will recreate the required output folders if they do not already exist.
