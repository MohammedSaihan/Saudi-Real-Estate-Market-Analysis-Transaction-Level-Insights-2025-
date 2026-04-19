# Saudi Real Estate Market Analysis (2025)

A data analytics project built with **Python (Pandas)** and **Power BI** to analyze real estate transactions across Saudi Arabia using quarterly 2025 data. The workflow starts in a Jupyter notebook for data loading, translation, cleaning, and feature engineering, then moves into Power BI for interactive market analysis and investment-focused dashboards.

---

## Project Overview

This project analyzes Saudi real estate transactions from **Q1 to Q4 2025** to uncover:

- market activity across major cities
- price movement by quarter
- average price per square meter
- transaction volume and deal distribution
- city-level investment opportunities
- property-type comparisons across markets

The goal is not just to show charts, but to turn raw Arabic government-style transaction data into a dashboard that supports **market understanding, pricing analysis, and location-based investment decisions**.

---

## Files in This Project

- **`RealEstateAnalysis (1).pbix`** — Power BI dashboard file
- **`load_data.ipynb`** — Jupyter notebook used for data ingestion, cleaning, translation, and exporting the final dataset

---

## Data Pipeline

The notebook handles the full preprocessing workflow before Power BI:

### 1. Load quarterly raw files
The notebook reads separate CSV files for:
- Q1 2025
- Q2 2025
- Q3 2025
- Q4 2025

These files are combined into one unified dataset.

### 2. Translate Arabic column names to English
Arabic fields are renamed into analyst-friendly English names such as:

- `region_ar`
- `city_ar`
- `transaction_date_gregorian`
- `property_type_ar`
- `property_count`
- `price_sar`
- `area_sqm`

### 3. Create English mapping columns
The notebook creates helper columns including:

- `property_type_en`
- `region_en`
- `city_en`
- `city_final`
- `city_clean`

This is important because the raw data contains Arabic text, spelling variation, and mixed naming conventions.

### 4. Clean numeric columns
The notebook converts:

- `price_sar` → numeric
- `area_sqm` → numeric

Then it removes invalid rows such as:

- `area_sqm <= 0`
- `price_sar <= 0`

### 5. Engineer core metric
A key analytical feature is created:

- **`price_per_sqm = price_sar / area_sqm`**

### 6. Handle city-name inconsistency
A large part of the work is cleaning city names and fixing Arabic/English inconsistencies such as:

- `جده` → `Jeddah`
- `بريده` → `Buraydah`
- `الهفوف` → `Hofuf`
- `الظهران` → `Dhahran`
- `الزلفي` → `Zulfi`

This step matters because bad city labels destroy grouping quality in Power BI.

### 7. Remove extreme outliers
The notebook filters out extreme values in `price_per_sqm` using the **99th percentile**, creating a cleaner dataset for more realistic market comparison.

### 8. Export cleaned data
The final cleaned file is exported as:

- **`saudi_real_estate_cleaned_2025.csv`**

---

## Dataset Snapshot

Based on the notebook outputs:

- **Total cleaned transactions after basic filtering:** `183,305`
- **Transactions after outlier trimming:** `181,353`
- **Total transaction value:** `116,493,922,343 SAR`
- **Average price per sqm:** `1,898.15 SAR`

### Quarterly transaction value
- **Q1:** `39.20B SAR`
- **Q2:** `24.53B SAR`
- **Q3:** `27.30B SAR`
- **Q4:** `25.46B SAR`

### Quarterly transaction count
- **Q1:** `59,340`
- **Q2:** `38,927`
- **Q3:** `44,693`
- **Q4:** `40,345`

---

## Key Findings from the Notebook

### Top cities by transaction count
- Riyadh — `30,527`
- Jeddah — `29,789`
- Madinah — `10,340`
- Makkah — `9,085`
- Buraydah — `5,701`

### Top cities by transaction value
- Jeddah — `28.79B SAR`
- Riyadh — `28.13B SAR`
- Makkah — `7.75B SAR`
- Madinah — `6.67B SAR`
- Dammam — `4.49B SAR`

### Top cities by average price per sqm
(among cities with meaningful transaction volume)
- Riyadh — `3,023.48 SAR`
- Jeddah — `2,965.33 SAR`
- Khobar — `2,898.18 SAR`
- Dammam — `2,582.11 SAR`
- Makkah — `2,355.19 SAR`

### Property type pattern
The dataset is dominated by **Residential** transactions, with much smaller Commercial and Agricultural segments.

---

## Power BI Dashboard Structure

The PBIX file contains **3 report pages**.

### 1. Market Analysis
This is the main overview page and includes visuals such as:

- **Relationship Price with Area** — scatter chart comparing `area_sqm` vs `price_sar` by property type
- **Scatter Chart City** — city slicer
- **Scatter Chart Property type** — property type slicer
- **Current Prices per Quarter** — line chart by quarter and city
- **Growth Per Quarter** — growth comparison by quarter and city
- **Riyadh Market Opportunity** — neighborhood-level average total price analysis
- **Avg. Price Per sqm VS Transaction Volume** — neighborhood comparison of pricing and volume

### 2. Investment Comparison Page
Although the file still labels this page as **Page 2**, the visuals clearly show it is an investment comparison view:

- **Compare Avg. Investment and Avg. Size**
- **Compare Cost Per Meter and Avg. Size**
- **Compare Avg. Investment and Property Type**

This page is useful for comparing city-level investment ticket size, average property size, and cost efficiency.

### 3. City Performance Page
This page focuses on city-level market performance and includes:

- **Relation Avg. Price and Volume**
- **Top 10 Cities by Volume**
- **Average Price Per SQM By City**
- **Total Deals per City**
- multiple city filters for focused exploration

---

## Inferred Power BI Measures / KPIs

From the report metadata, the dashboard appears to use measures such as:

- `avg_price_sqm`
- `transaction_volume`
- `avg_total_price`
- `current_q_price`
- `pct_growth`
- `average_investment_ticket`
- `cost_per_meter`
- `total_volume_sar`
- `total_deals`
- `avg_size`

These measures support pricing trends, deal activity, and investment comparison.

---

## Business Questions This Project Answers

- Which Saudi cities show the highest real estate activity?
- Where is transaction value concentrated?
- Which markets have the highest average price per square meter?
- How do prices change across quarters?
- Which neighborhoods in Riyadh look stronger for market opportunity?
- How do property types compare in average investment size?
- Which cities combine volume and pricing strength?

---

## Tools Used

- **Python**
- **Pandas**
- **Jupyter Notebook**
- **Power BI**

---

## Why This Project Matters

This project shows practical analyst skills, not tutorial-level fluff:

- handling messy multilingual data
- translating raw fields into business-ready dimensions
- fixing inconsistent city labels
- filtering unrealistic outliers
- engineering market metrics
- turning a large transactional dataset into an interactive decision-making dashboard

This is the kind of project that demonstrates readiness for roles in:

- Data Analytics
- Business Intelligence
- Real Estate Analytics
- Market Research
- Investment Analysis

---

## Weak Points / Honest Notes

A few things are good but still need tightening if this project is going into a portfolio:

1. **Two report pages still have generic names** (`Page 2`, `Page 3`). That looks unfinished.
2. **City translation is still partially incomplete** in the notebook. You clearly improved it a lot, but some Arabic city names remain unmapped.
3. The notebook shows several **`SettingWithCopyWarning`** messages. It works, but it is sloppy and should be cleaned using `.copy()` and `.loc[]` consistently.
4. Some city mapping values look suspicious or potentially incorrect, so those should be audited before presenting the project as production-grade.

---

## Suggested Next Improvements

- Rename Power BI pages to business-friendly names
- Add a dedicated **Executive Summary** page with KPI cards
- Standardize all remaining Arabic city names
- Create a proper data dictionary
- Add DAX measure documentation
- Add screenshots of each report page to this README
- Add a short section explaining the raw data source

---

## Recommended Portfolio Title

**Saudi Real Estate Market Analysis 2025 | Python + Power BI Dashboard**

---

## Author1

**Mujtaba Almeshal**  
Data Analyst | SQL | Power BI | Python
[LinkedIn Profile](https://www.linkedin.com/in/mujtaba-almeshal/)



## Author2

**Mohammed Saihan**  
Data Analyst | SQL | Power BI | Python
[LinkedIn Profile](https://www.linkedin.com/in/mohammed-saihan/)