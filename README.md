# 🧹 Data Cleaning & Exploratory Data Analysis
**Data Science Internship — SWYNEX Technologies**

**Author:** Affan Inamdar
**Domain:** Data Science / Data Analytics
**Tools Used:** Python · Pandas · NumPy · Matplotlib · Seaborn · Jupyter Notebook

---

## 📌 Tasks Overview

| Task | Description | Status |
|------|-------------|--------|
| Task 1 | Data Cleaning & Preparation | ✅ Complete |
| Task 2 | Exploratory Data Analysis (EDA) | ✅ Complete |

---

## 📊 Dataset Used

- **Dataset:** Sales Dataset (Real-world Sales Transactions)
- **Raw Records:** 2,823 rows × 25 columns
- **Domain:** Sales / Business Analytics
- **Format:** CSV
- **Columns Include:** Employee_ID, Employee_Name, Gender, Age, City, Region, Company, Department, Designation, Salary, Product, Category, Quantity, Unit_Price, Discount_Percent, Final_Sale_Amount, Order_Date, Payment_Method, Order_Status, Customer_Rating

---

## 📁 Repository Structure

```
data-cleaning-task/
│
├── raw_data.csv                    ← Original untouched sales dataset
├── cleaned_data.csv                ← Final cleaned output (Task 1)
│
├── data_cleaning.ipynb             ← Task 1: Complete cleaning notebook
├── eda_analysis_FIXED.ipynb        ← Task 2: Complete EDA notebook
│
├── Screenshots/
│   ├── 01_libraries_imported.png
│   ├── 02_raw_data_head.png
│   ├── 03_raw_data_info.png
│   ├── 04_missing_values_report.png
│   ├── 05_missing_values_heatmap.png
│   ├── 06_missing_values_fixed.png
│   ├── 07_duplicates_removed.png
│   ├── 08_datatypes_fixed.png
│   ├── 09_outliers_handled.png
│   ├── 10_cleaning_summary_report.png
│   ├── 11_quality_dashboard_chart.png
│   ├── 12_cleaned_data_saved.png
│   ├── eda_chart1_distribution.png
│   ├── eda_chart2_revenue_by_city.png
│   ├── eda_chart3_revenue_by_category.png
│   ├── eda_chart4_sales_trend.png
│   ├── eda_chart5_correlation.png
│   ├── eda_chart6_outliers.png
│   ├── eda_chart7_payment_status.png
│   └── eda_chart8_summary_dashboard.png
│
└── README.md                       ← Project documentation
```

---

## ✅ Task 1 — Data Cleaning & Preparation

### Objective
Clean and prepare the raw Sales Dataset for analysis by identifying and fixing all data quality issues.

### Cleaning Steps Performed

| # | Step | Issue Found | Action Taken |
|---|------|-------------|--------------|
| 1 | Missing Values | Missing values across multiple columns | Numeric → filled with Median; Categorical → filled with Mode |
| 2 | Duplicate Records | Exact duplicate rows found | Removed duplicates, kept first occurrence |
| 3 | Data Type Fixes | Date columns stored as object strings | Converted using `pd.to_datetime()` |
| 4 | Inconsistent Values | Mixed case text (mumbai / Mumbai / MUMBAI) | Standardised using `str.strip()` + `str.title()` |
| 5 | Outliers | Extreme values in numeric columns | Capped using IQR method (Winsorization) |
| 6 | Invalid Values | Negative values in price/quantity columns | Converted to positive using `abs()` |
| 7 | Derived Columns | No grouped or aggregated features | Added Age_Group, Salary_Band, Year, Month, Quarter |

### Before vs After

| Metric | Before Cleaning | After Cleaning |
|--------|----------------|----------------|
| Total Rows | 2,823 | Cleaned ✅ |
| Missing Values | Multiple columns | 0 ✅ |
| Duplicate Rows | Present | 0 ✅ |
| Data Type Issues | Multiple columns | All fixed ✅ |
| Inconsistent Values | Present | Standardised ✅ |
| Outliers | Present | Capped via IQR ✅ |
| Data Quality | Raw / Unprocessed | Clean / Analysis-Ready ✅ |

### Task 1 Screenshots

#### Missing Values Heatmap (Before Cleaning)
<img width="1085" height="453" alt="05_missing_values_heatmap" src="https://github.com/user-attachments/assets/10635e06-bbfe-495f-b4ae-a687fed1deae"/>

#### Data Quality Dashboard (After Cleaning)
<img width="711" height="897" alt="11_quality_dashboard_chart" src="https://github.com/user-attachments/assets/a5f3cbc5-85b2-4517-bd7d-79b69a38db12"/>

---

## ✅ Task 2 — Exploratory Data Analysis (EDA)

### Objective
Perform exploratory analysis on the cleaned Sales Dataset to calculate statistics, identify trends, patterns and anomalies, and extract at least 5 useful business insights.

### 7 Key Insights Discovered

| # | Insight | Finding |
|---|---------|---------|
| 1 | Revenue Distribution | Revenue is right-skewed — most orders are below average value; a few large orders drive the mean up |
| 2 | Revenue by City/Region | Revenue is unevenly distributed — top cities generate significantly more than bottom cities |
| 3 | Product/Category Performance | Top 5 categories contribute to majority of total revenue (Pareto Principle — 80/20 rule observed) |
| 4 | Sales Trend Over Time | Clear monthly and quarterly revenue patterns — peak months and best quarter identified |
| 5 | Correlation Analysis | Strong positive correlations found between key numeric variables — discount and quantity are top revenue drivers |
| 6 | Outlier Detection | Outliers detected in revenue and quantity — represent premium transactions or potential data anomalies |
| 7 | Payment & Demographics | Most popular payment method identified; order completion rate and status distribution analysed |

### Charts Generated (8 Charts)

| Chart | File | Description |
|-------|------|-------------|
| Chart 1 | eda_chart1_distribution.png | Revenue Histogram + Box Plot |
| Chart 2 | eda_chart2_revenue_by_city.png | Revenue by City — Bar + Pie |
| Chart 3 | eda_chart3_revenue_by_category.png | Product/Category Revenue Analysis |
| Chart 4 | eda_chart4_sales_trend.png | Monthly & Quarterly Sales Trend |
| Chart 5 | eda_chart5_correlation.png | Correlation Heatmap |
| Chart 6 | eda_chart6_outliers.png | Outlier Detection Box Plots |
| Chart 7 | eda_chart7_payment_status.png | Payment Method & Order Status |
| Chart 8 | eda_chart8_summary_dashboard.png | **Final EDA Summary Dashboard ⭐** |

### Task 2 Screenshots

#### EDA Summary Dashboard
![EDA Summary Dashboard](Screenshots/eda_chart8_summary_dashboard.png)

#### Revenue by City
![Revenue by City](Screenshots/eda_chart2_revenue_by_city.png)

#### Correlation Heatmap
![Correlation](Screenshots/eda_chart5_correlation.png)

---

## 🛠️ How to Run This Project

### 1. Clone the repository
```bash
git clone https://github.com/affanazinamdar91/data-cleaning-task.git
cd data-cleaning-task
```

### 2. Install required libraries
```bash
pip install pandas numpy matplotlib seaborn jupyter
```

### 3. Run Task 1 — Data Cleaning
```bash
jupyter notebook data_cleaning.ipynb
```
→ Go to **Kernel → Restart & Run All**
→ Output: `cleaned_data.csv`

### 4. Run Task 2 — EDA
```bash
jupyter notebook eda_analysis_FIXED.ipynb
```
→ Go to **Kernel → Restart & Run All**
→ Output: 8 chart PNG files saved to Screenshots folder

---

## 💡 Key Libraries Used

| Library | Purpose |
|---------|---------|
| `pandas` | Data loading, manipulation, cleaning |
| `numpy` | Numerical operations, IQR calculation |
| `matplotlib` | Charts, dashboards, visualisations |
| `seaborn` | Heatmaps, distribution plots, correlation |

---

## 🔗 Connect

- **LinkedIn:** [linkedin.com/in/affan-inamdar-bb32a3342](https://linkedin.com/in/affan-inamdar-bb32a3342)
- **GitHub:** [github.com/affanazinamdar91](https://github.com/affanazinamdar91)
- **Email:** afaninamdar91@gmail.com

---

*Submitted as Task 1 & Task 2 — Data Science Internship @ SWYNEX Technologies*
