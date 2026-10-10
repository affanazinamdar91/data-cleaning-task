# 📊 Sales Analytics Case Study
## End-to-End Data Analytics Project
**Data Science Internship — SWYNEX Technologies**
**Author:** Affan Inamdar
**Duration:** September – October 2026
**Tools:** Python · Pandas · NumPy · Matplotlib · Seaborn · Power BI · Jupyter Notebook

---

## 📌 Table of Contents
1. [Problem Statement](#problem-statement)
2. [Dataset Information](#dataset-information)
3. [Task 1 — Data Cleaning](#task-1--data-cleaning--preparation)
4. [Task 2 — Exploratory Data Analysis](#task-2--exploratory-data-analysis)
5. [Task 3 — Interactive Dashboard](#task-3--interactive-power-bi-dashboard)
6. [Key Business Insights](#key-business-insights)
7. [Recommendations](#recommendations)
8. [Project Files](#project-files)
9. [How to Run](#how-to-run)

---

## 🎯 Problem Statement

A global sales company operating across 19 countries wanted to understand
its sales performance, identify revenue drivers, and make data-driven
decisions to improve profitability.

**Key Business Questions:**
- Which product lines generate the most revenue?
- Which territories and countries are the top performers?
- Who are the most valuable customers?
- What are the seasonal sales trends?
- How can the company improve order completion rates?
- What deal sizes drive the most revenue?

**Goal:** Build a complete analytics pipeline from raw data to
interactive dashboard that answers these questions clearly.

---

## 📊 Dataset Information

| Property | Details |
|----------|---------|
| Dataset Name | Global Sales Dataset |
| Source | Public Sales Transaction Records |
| Time Period | January 2003 — May 2005 |
| Raw Records | 2,823 rows × 25 columns |
| After Cleaning | 2,823 rows × 28 columns |
| Domain | B2B Sales / Global Commerce |
| Format | CSV |

### Column Description

| Column | Description | Type |
|--------|-------------|------|
| ORDERNUMBER | Unique order identifier | Numeric |
| QUANTITYORDERED | Units ordered per line | Numeric |
| PRICEEACH | Unit price | Numeric |
| SALES | Total sale amount per line | Numeric |
| ORDERDATE | Date of order | Date |
| STATUS | Order status (Shipped/Cancelled etc.) | Categorical |
| PRODUCTLINE | Product category | Categorical |
| CUSTOMERNAME | Customer company name | Text |
| COUNTRY | Customer country | Categorical |
| TERRITORY | Sales territory (EMEA/APAC/Japan) | Categorical |
| DEALSIZE | Deal size (Small/Medium/Large) | Categorical |
| MSRP | Manufacturer suggested retail price | Numeric |
| YEAR_ID | Year of order | Numeric |
| MONTH_ID | Month of order | Numeric |
| QTR_ID | Quarter of order | Numeric |

---

## 🧹 Task 1 — Data Cleaning & Preparation

### Objective
Transform raw sales data into a clean, analysis-ready dataset.

### Issues Found & Fixed

| # | Issue | Details | Solution |
|---|-------|---------|---------|
| 1 | Missing Values | Null values in multiple columns | Numeric → Median fill; Categorical → Mode fill |
| 2 | Duplicate Records | Exact duplicate rows | Removed, kept first occurrence |
| 3 | Data Type Errors | Date columns stored as strings | Converted using pd.to_datetime() |
| 4 | Inconsistent Text | Mixed case values (usa/USA/Usa) | Standardised using str.strip() + str.title() |
| 5 | Outliers | Extreme values in SALES, QUANTITYORDERED | Capped using IQR method (Winsorization) |
| 6 | Invalid Values | Negative values in numeric columns | Converted using abs() |
| 7 | Missing Features | No time-based derived columns | Added Year, Month, Quarter columns |

### Before vs After

| Metric | Before | After |
|--------|--------|-------|
| Missing Values | Present | 0 ✅ |
| Duplicate Rows | Present | 0 ✅ |
| Data Type Issues | Multiple | All Fixed ✅ |
| Inconsistent Values | Present | Standardised ✅ |
| Columns | 25 | 28 (3 derived added) ✅ |

### Derived Columns Added
- `ORDERDATE_Year` — Year extracted from order date
- `ORDERDATE_Month` — Month name extracted
- `ORDERDATE_Quarter` — Quarter (Q1/Q2/Q3/Q4)

### Code
```python
# Missing values
df.fillna(df.median(numeric_only=True), inplace=True)
df.fillna(df.mode().iloc[0], inplace=True)

# Duplicates
df.drop_duplicates(keep='first', inplace=True)

# Data types
df['ORDERDATE'] = pd.to_datetime(df['ORDERDATE'], errors='coerce')

# Outliers — IQR method
Q1 = df['SALES'].quantile(0.25)
Q3 = df['SALES'].quantile(0.75)
IQR = Q3 - Q1
df['SALES'] = df['SALES'].clip(Q1 - 1.5*IQR, Q3 + 1.5*IQR)
```

### Screenshots
![Missing Values Heatmap](Screenshots/05_missing_values_heatmap.png)
![Cleaning Summary](Screenshots/11_quality_dashboard_chart.png)

---

## 🔍 Task 2 — Exploratory Data Analysis

### Objective
Analyse the cleaned dataset to find trends, patterns, and anomalies.
Extract at least 5 key business insights.

### Dataset Overview After Cleaning

| KPI | Value |
|-----|-------|
| Total Revenue | $9,934,834 |
| Total Orders | 307 |
| Total Quantity Sold | 98,976 units |
| Average Order Value | $3,519 |
| Total Countries | 19 |
| Total Customers | 92 |
| Total Products | 109 |
| Date Range | Jan 2003 — May 2005 |

---

### 🔍 Insight 1 — Revenue Distribution is Right-Skewed

The SALES column has:
- Mean: $3,519
- Median: $3,185
- Std Dev: $1,731
- Skewness: Positive (right-skewed)

**Finding:** Most orders are below the average value.
A small number of large orders pull the mean upward.
This indicates a concentration of high-value transactions.

![Distribution Chart](Screenshots/eda_chart1_distribution.png)

---

### 🔍 Insight 2 — EMEA Dominates Revenue (88% Market Share)

| Territory | Revenue | Share |
|-----------|---------|-------|
| EMEA | $8,745,287 | 88.0% |
| APAC | $741,615 | 7.5% |
| Japan | $447,932 | 4.5% |

**Finding:** EMEA territory generates 88% of all revenue.
APAC and Japan are significantly underpenetrated markets
with high growth potential.

![Revenue by Territory](Screenshots/eda_chart2_revenue_by_city.png)

---

### 🔍 Insight 3 — Classic Cars Drive 39% of Total Revenue

| Product Line | Revenue | Share |
|-------------|---------|-------|
| Classic Cars | $3,865,485 | 38.9% |
| Vintage Cars | $1,879,004 | 18.9% |
| Motorcycles | $1,154,422 | 11.6% |
| Trucks & Buses | $1,125,623 | 11.3% |
| Planes | $970,632 | 9.8% |
| Ships | $714,437 | 7.2% |
| Trains | $225,231 | 2.3% |

**Finding:** Classic Cars alone generate 39% of all revenue.
Top 2 product lines (Classic + Vintage Cars) account for 58%
of total revenue — a clear Pareto pattern (80/20 rule).

![Product Line Revenue](Screenshots/eda_chart3_revenue_by_category.png)

---

### 🔍 Insight 4 — 2004 was the Peak Revenue Year

| Year | Revenue | Growth |
|------|---------|--------|
| 2003 | $3,497,608 | Baseline |
| 2004 | $4,687,796 | +34% ✅ |
| 2005 | $1,749,431 | -63% ⚠️ (partial year) |

**Finding:** Revenue grew 34% from 2003 to 2004.
2005 shows only 5 months of data (Jan–May)
so the drop is expected — not a real decline.

![Sales Trend](Screenshots/eda_chart4_sales_trend.png)

---

### 🔍 Insight 5 — Strong Positive Correlation Between Price and Sales

Correlation analysis shows:
- PRICEEACH vs SALES: Strong positive correlation
- QUANTITYORDERED vs SALES: Strong positive correlation
- MSRP vs PRICEEACH: Moderate positive correlation

**Finding:** Higher priced items tend to generate more revenue
per order. Pricing strategy directly impacts total sales.

![Correlation Heatmap](Screenshots/eda_chart5_correlation.png)

---

### 🔍 Insight 6 — 92.7% Order Completion Rate

| Status | Count | Percentage |
|--------|-------|-----------|
| Shipped | 2,617 | 92.7% ✅ |
| Cancelled | 60 | 2.1% |
| Resolved | 47 | 1.7% |
| On Hold | 44 | 1.6% |
| In Process | 41 | 1.5% |
| Disputed | 14 | 0.5% |

**Finding:** 92.7% completion rate is strong.
However 2.1% cancellation rate needs investigation.
74 orders (2.6%) are in problematic states (On Hold/Disputed).

![Order Status](Screenshots/eda_chart6_outliers.png)

---

### 🔍 Insight 7 — Top 2 Customers = 15.5% of Total Revenue

| Customer | Revenue | Share |
|----------|---------|-------|
| Euro Shopping Channel | $902,218 | 9.1% |
| Mini Gifts Distributors Ltd. | $647,303 | 6.5% |
| Australian Collectors, Co. | $197,886 | 2.0% |
| Muscle Machine Inc | $194,249 | 2.0% |
| La Rochelle Gifts | $178,050 | 1.8% |

**Finding:** Top 2 customers alone generate 15.5% of revenue.
High customer concentration = high business risk.
Losing one key customer significantly impacts total revenue.

![Payment Status](Screenshots/eda_chart7_payment_status.png)

---

### EDA Summary Dashboard
![EDA Dashboard](Screenshots/eda_chart8_summary_dashboard.png)

---

## 📈 Task 3 — Interactive Power BI Dashboard

### Objective
Build a professional 2-page interactive dashboard to communicate
all findings visually to business stakeholders.

### Dashboard Structure

#### Page 1 — Executive Overview
| Visual | Type | Insight Shown |
|--------|------|--------------|
| Total Revenue KPI | Card | $9.93M total |
| Total Orders KPI | Card | 307 orders |
| Total Quantity KPI | Card | 99K units |
| Avg Order Value KPI | Card | $3.52K |
| Completion Rate KPI | Card | 92.7% |
| Revenue by City | Bar Chart | Top cities |
| Revenue by Product Line | Donut Chart | Category share |
| Monthly Revenue Trend | Line Chart | Seasonality |
| Revenue by Territory | Column Chart | Geographic split |

#### Page 2 — Sales Analysis
| Visual | Type | Insight Shown |
|--------|------|--------------|
| Top 10 Customers | Bar Chart | Key accounts |
| Revenue by Deal Size | Column Chart | Deal segmentation |
| Quarterly Revenue | Column Chart | Q1-Q4 performance |
| Order Status | Donut Chart | Completion rate |

### Interactive Features
- 5 slicers (Territory, Product Line, Year, Status, Deal Size)
- Cross-visual filtering — click any chart to filter all others
- 8 DAX measures
- 3 calculated columns

### DAX Measures Built
```dax
Total Revenue    = SUM(cleaned_data[SALES])
Total Orders     = DISTINCTCOUNT(cleaned_data[ORDERNUMBER])
Total Quantity   = SUM(cleaned_data[QUANTITYORDERED])
Avg Order Value  = AVERAGE(cleaned_data[SALES])
Avg Unit Price   = AVERAGE(cleaned_data[PRICEEACH])
Completion Rate  = DIVIDE(COUNTROWS(FILTER(...,"Shipped")),COUNTROWS(...),0)*100
Large Deals      = COUNTROWS(FILTER(cleaned_data,DEALSIZE="Large"))
Revenue per Line = DIVIDE(SUM(cleaned_data[SALES]),COUNTROWS(cleaned_data),0)
```

### Dashboard Screenshots
![Page 1](Screenshots/task3_page1_executive_overview.png)
![Page 2](Screenshots/task3_page2_sales_analysis.png)

---

## 💡 Key Business Insights

### Top 7 Findings

| # | Insight | Impact |
|---|---------|--------|
| 1 | EMEA generates 88% of revenue | High geographic concentration risk |
| 2 | Classic Cars = 39% of revenue | Single product line dependency |
| 3 | Top 2 customers = 15.5% revenue | Customer concentration risk |
| 4 | 2004 was peak year (+34% growth) | Growth trend established |
| 5 | 92.7% order completion rate | Strong operational performance |
| 6 | Medium deals = 61% of revenue | Core segment identified |
| 7 | Price strongly correlates with sales | Pricing strategy matters |

---

## ✅ Recommendations

Based on the analysis, here are 7 data-driven recommendations:

### 1. 🌏 Expand into APAC and Japan
APAC (7.5%) and Japan (4.5%) are massively underpenetrated.
Targeted sales campaigns in Australia, Singapore, and Japan
could add $2M+ in revenue annually.

### 2. 🚗 Protect Classic Cars Revenue
Classic Cars drive 39% of revenue. Any disruption to this
product line severely impacts the business. Diversify by
growing Motorcycles and Trucks categories.

### 3. 👥 Reduce Customer Concentration Risk
Top 2 customers = 15.5% of revenue. Losing either is
catastrophic. Invest in acquiring 10+ new medium-sized
accounts to distribute revenue risk.

### 4. 📅 Capitalise on Q4 Seasonality
Revenue peaks in Q4 every year. Plan inventory, staffing,
and marketing campaigns 3 months in advance to maximise
Q4 performance.

### 5. 💰 Focus on Medium Deal Customers
Medium deals generate 61% of revenue with 1,384 transactions.
Create a dedicated medium-account sales team and loyalty
program to retain these customers.

### 6. ✅ Investigate Cancelled Orders
60 cancelled orders = $0 revenue that could have been earned.
Root cause analysis on cancellations could recover
$200K+ in lost revenue annually.

### 7. 🇺🇸 Double Down on USA Market
USA generates $3.59M (36% of total). With the right
investment in US sales team, this market could reach $5M+.

---

## 📁 Project Files

```
data-cleaning-task/
│
├── raw_data.csv                      ← Original dataset
├── cleaned_data.csv                  ← Cleaned dataset (Task 1 output)
├── data_cleaning.ipynb               ← Task 1: Cleaning notebook
├── eda_analysis_FIXED.ipynb          ← Task 2: EDA notebook
├── Sales_Analytics_Dashboard.pbix    ← Task 3: Power BI dashboard
├── Sales_Analytics_Dashboard.pdf     ← Task 3: Dashboard PDF export
├── CASE_STUDY.md                     ← This file
│
└── Screenshots/
    ├── 01_libraries_imported.png
    ├── 02_raw_data_head.png
    ├── 03_raw_data_info.png
    ├── 04_missing_values_report.png
    ├── 05_missing_values_heatmap.png
    ├── 06_missing_values_fixed.png
    ├── 07_duplicates_removed.png
    ├── 08_datatypes_fixed.png
    ├── 09_outliers_handled.png
    ├── 10_cleaning_summary_report.png
    ├── 11_quality_dashboard_chart.png
    ├── 12_cleaned_data_saved.png
    ├── eda_chart1_distribution.png
    ├── eda_chart2_revenue_by_city.png
    ├── eda_chart3_revenue_by_category.png
    ├── eda_chart4_sales_trend.png
    ├── eda_chart5_correlation.png
    ├── eda_chart6_outliers.png
    ├── eda_chart7_payment_status.png
    ├── eda_chart8_summary_dashboard.png
    ├── task3_page1_executive_overview.png
    └── task3_page2_sales_analysis.png
```

---

## 🛠️ How to Run

### Prerequisites
```bash
pip install pandas numpy matplotlib seaborn jupyter
```

### Task 1 — Data Cleaning
```bash
jupyter notebook data_cleaning.ipynb
# Kernel → Restart & Run All
# Output: cleaned_data.csv
```

### Task 2 — EDA
```bash
jupyter notebook eda_analysis_FIXED.ipynb
# Kernel → Restart & Run All
# Output: 8 chart PNG files in Screenshots folder
```

### Task 3 — Dashboard
```
Open Sales_Analytics_Dashboard.pbix in Power BI Desktop
Use slicers to interact with all charts
```

---

## 💡 Tech Stack

| Tool | Purpose |
|------|---------|
| Python 3.10 | Core programming language |
| Pandas | Data manipulation and cleaning |
| NumPy | Numerical operations and IQR |
| Matplotlib | Data visualisation |
| Seaborn | Statistical plots and heatmaps |
| Jupyter Notebook | Interactive development |
| Power BI Desktop | Interactive dashboard |
| DAX | Business calculations |
| Git & GitHub | Version control |

---

## 🔗 Connect

- **LinkedIn:** [linkedin.com/in/affan-inamdar-bb32a3342](https://linkedin.com/in/affan-inamdar-bb32a3342)
- **GitHub:** [github.com/affanazinamdar91](https://github.com/affanazinamdar91)
- **Email:** afaninamdar91@gmail.com

---

*Final Project — Data Science Internship @ SWYNEX Technologies*
*Author: Affan Inamdar | 2026*
