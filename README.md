# 🧹 Task 1 — Data Cleaning & Preparation

**Author:** Affan Inamdar  
**Domain:** Data Science / Data Analytics  
**Tools Used:** Python · Pandas · NumPy · Matplotlib · Seaborn · Jupyter Notebook

---

## 📌 Objective

Clean and prepare a raw **Sales Dataset** for analysis by identifying and fixing common data-quality issues, including:

- Missing values
- Duplicate records
- Incorrect data types
- Inconsistent / dirty values
- Outliers
- Invalid or negative values

The goal of this project is to transform the raw sales data into a clean and analysis-ready dataset.

---

## 📁 Repository Structure


data-cleaning-task/
│
├── data/
│   ├── raw_data.csv              ← Original untouched sales dataset
│   └── cleaned_data.csv          ← Final cleaned sales dataset
│
├── notebooks/
│   └── data_cleaning.ipynb       ← Complete cleaning notebook
│
├── screenshots/
│   ├── missing_values_heatmap.png
│   └── cleaning_summary_chart.png
│
└── README.md                     ← Project documentation

## 📊 Dataset Used

- **Dataset:** Sales Dataset
- **Records:** Sales transaction records
- **Domain:** Sales / Business Analytics
- **Format:** CSV
- **Purpose:** Data cleaning, preprocessing, and preparation for analysis

The dataset contains sales-related information and was used to demonstrate practical data-cleaning and preprocessing techniques.

---

## 🔧 Cleaning Steps Performed

| # | Step | Issue Found | Action Taken |
|---|------|-------------|--------------|
| 1 | Missing Values | Missing values identified across relevant columns | Missing values were handled using appropriate imputation or removal techniques |
| 2 | Duplicate Records | Duplicate rows identified during data-quality checks | Duplicate records were removed while retaining valid records |
| 3 | Data Type Fixes | Some columns had inappropriate data types | Converted columns to appropriate numeric, categorical, and date formats |
| 4 | Inconsistent Values | Inconsistent formatting and categorical values | Standardised text and categorical values for consistency |
| 5 | Outliers | Extreme values identified in numerical columns | Outliers were identified and handled using the IQR method |
| 6 | Invalid Values | Invalid or negative values checked in numerical columns | Invalid values were identified and handled appropriately |
| 7 | Derived Columns | Additional analytical fields required | Created derived columns where required for further analysis |

---

## 📈 Before vs After Comparison

| Metric | Before Cleaning | After Cleaning |
|--------|----------------|----------------|
| Total Rows | Raw dataset | Cleaned dataset |
| Missing Values | Identified | Handled |
| Duplicate Rows | Identified | Removed |
| Data Type Issues | Identified | Corrected |
| Inconsistent Values | Identified | Standardised |
| Outliers | Identified | Handled |
| Data Quality | Raw / Unprocessed | Clean / Analysis-Ready |

---

## 🛠️ How to Run This Project

### 1. Clone the repository


git clone https://github.com/affanazinamdar91/data-cleaning-task.git
cd data-cleaning-task

## 📸 Screenshots

### Missing Values Heatmap (Before Cleaning)
![Missing Values](<img width="1085" height="453" alt="05_missing_values_heatmap png" src="https://github.com/user-attachments/assets/10635e06-bbfe-495f-b4ae-a687fed1deae" />
)

### Data Quality Dashboard (After Cleaning)
![Cleaning Summary](<img width="711" height="897" alt="11_quality_dashboard_chart png" src="https://github.com/user-attachments/assets/a5f3cbc5-85b2-4517-bd7d-79b69a38db12" />
)

---

## 🔗 Connect

- **LinkedIn:** [linkedin.com/in/affan-inamdar-bb32a3342](https://linkedin.com/in/affan-inamdar-bb32a3342)
- **GitHub:** [github.com/affanazinamdar91](https://github.com/affanazinamdar91)
- **Email:** afaninamdar91@gmail.com

---

*Submitted as Task 1 — Data Science Internship*
