# End-to-End Sales & Revenue Analytics (Remittance Case Study — 2025)

## Overview
This project simulates the daily work of a Data Analyst at a fintech/remittance company (inspired by Intermex).

The goal was to build a full analytics pipeline — starting from raw CSV transaction files, loading into PostgreSQL (`financial_db`), cleaning and transforming with SQL, validating with Excel, and visualizing insights in Power BI.

The final deliverable is an interactive dashboard showing sales performance, fee revenue, agent performance, customer trends, and payment method preferences.

## Dataset
The dataset is synthetic but modeled on real-world remittance data.

**Files included:**
- `transactions.csv` → Fact table (transaction-level details)
- `customers.csv` → Customer demographics & signup data
- `agents.csv` → Agent network information
- `calendar_2025.csv` → Date dimension (Jan–Dec 2025)
- `sales_targets.csv` → Monthly sales and revenue targets

**Fact–Dimension structure:**
- **Fact:** `transactions`
- **Dimensions:** `customers`, `agents`, `calendar_2025`, `sales_targets`

## Process
### 1. Quick QA in Excel
- Checked for duplicates, nulls, and formatting errors.
- Built pivot tables for Revenue by Month and Transactions by Country as a first validation step.

### 2. CSV → PostgreSQL (via Jupyter)
- Used Pandas + SQLAlchemy in Jupyter to load all CSVs into `financial_db`.
- Ensured consistent datatypes (dates, integers, currency fields).

### 3. SQL Cleaning & Transformation
- Standardized column names, removed duplicates, and imputed missing values.
- Converted boolean/text fields into business-readable formats (e.g., Completed, Failed).
- Created summary tables for KPIs: Total Fee Revenue, Transaction Volume, Avg Transaction Value, Agent & Regional performance.

### 4. EDA & KPI Queries
- Built SQL queries to extract:
  - Monthly revenue trends
  - Agent performance (Actual vs Target)
  - Customer activity levels
  - Payment method breakdown

### 5. Cross-check in Excel
- Exported summary tables back into Excel.
- Verified totals matched SQL and dashboard results.

### 6. Power BI Visualization
- Imported cleaned tables into Power BI (Star Schema).
- Created DAX measures for Fee Revenue, Transaction Volume, Avg Value, and Active Customers.
- Designed a recruiter-friendly dashboard with minimal but impactful visuals.

## Dashboard Highlights
**KPIs (top-level):**
- Total Fee Revenue
- Total Transaction Volume
- Average Transaction Value
- Active Customers

**Visuals:**
- Line chart — Monthly Fee Revenue trend
- Bar chart — Top Agents by Revenue
- Gauge — Revenue vs Target
- Treemap/Map — Revenue by Country/State
- Donut — Payment Method distribution
- Stacked bar — Transaction Status (Completed/Failed/Refunded)

**Filters/Slicers:** Date, Agent, Country, Customer Type, Channel

## Deliverables
- `notebooks/load_to_postgres.ipynb` → ETL (Excel/CSV → PostgreSQL)
- `sql/01_data_cleaning.sql` → Cleaning & transformations
- `sql/02_eda_kpis.sql` → KPI/summary queries
- `excel/financial_data_analysis.xlsx` → QA pivots & checks
- `powerbi/financial_dashboard.pbix` → Final dashboard
- `images/dashboard_preview.png` → Screenshot of dashboard

## How to Run
### Database setup
1. Create PostgreSQL DB: `financial_db`
2. Run `notebooks/load_to_postgres.ipynb` to load CSVs

### Run SQL scripts
1. Execute `sql/01_data_cleaning.sql` → cleaning
2. Execute `sql/02_eda_kpis.sql` → KPIs

### Validation (optional)
- Open `excel/financial_data_analysis.xlsx` → check pivots

### Open dashboard
- Open `powerbi/financial_dashboard.pbix` → connect to `financial_db` or use exported summary CSVs

## Key Insights
- A few agents drive the majority of fee revenue → coaching/incentive opportunities.
- Card & bank transfers yield higher revenue compared to cash.
- Americas dominate transaction volume → expansion opportunity in underrepresented regions.
- Failed/refunded transactions highlight friction points in payments/agent training.

