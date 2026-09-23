# 🧹 Task 1 — Data Cleaning & Preparation

**Author:** Affan Inamdar  
**Domain:** Data Science / Data Analytics  
**Tools Used:** Python · Pandas · NumPy · Matplotlib · Seaborn · Jupyter Notebook

---

## 📌 Objective

Clean and prepare a raw dataset for analysis by identifying and fixing:
- Missing values
- Duplicate records
- Incorrect data types
- Inconsistent / dirty values
- Outliers

---

## 📁 Repository Structure

```
data-cleaning-task/
│
├── data/
│   ├── raw_data.csv          ← Original untouched dataset
│   └── cleaned_data.csv      ← Final cleaned output
│
├── notebooks/
│   └── data_cleaning.ipynb   ← Complete cleaning notebook (step-by-step)
│
├── screenshots/
│   ├── missing_values_heatmap.png    ← Before cleaning visualisation
│   └── cleaning_summary_chart.png   ← After cleaning quality dashboard
│
└── README.md                 ← This file
```

---

## 📊 Dataset Used

- **Source:** [Titanic Dataset — Kaggle](https://www.kaggle.com/datasets/yasserh/titanic-dataset)
- **Records:** 891 rows × 12 columns (raw)
- **Domain:** Passenger survival data — ideal for demonstrating cleaning techniques

---

## 🔧 Cleaning Steps Performed

| # | Step | Issue Found | Action Taken |
|---|------|-------------|--------------|
| 1 | Missing Values | Age (19.9%), Cabin (77.1%), Embarked (0.2%) | Age → filled with median; Cabin → dropped (too many missing); Embarked → filled with mode |
| 2 | Duplicate Records | Checked all rows for exact duplicates | Removed duplicates, kept first occurrence |
| 3 | Data Type Fixes | PassengerId, Pclass stored incorrectly | Converted to correct types using pd.to_numeric() and pd.to_datetime() |
| 4 | Inconsistent Values | Gender values mixed case (male/Male/MALE) | Standardised to Title Case using str.title() |
| 5 | Outliers | Fare column had extreme outliers (£512) | Capped using IQR method (Winsorization) |
| 6 | Negative Values | Checked Age, Fare for negatives | Converted any negatives to positive using abs() |
| 7 | Derived Columns | No age groups or fare bands | Added Age_Group and Fare_Band columns for analysis |

---

## 📈 Before vs After Comparison

| Metric | Before Cleaning | After Cleaning |
|--------|----------------|----------------|
| Total Rows | 891 | 889 |
| Missing Values | 866 | 0 |
| Duplicate Rows | 2 | 0 |
| Columns | 12 | 15 |
| Data Type Issues | 3 columns | 0 |
| Outliers Capped | — | Yes (Fare column) |

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

### 3. Open the notebook
```bash
jupyter notebook notebooks/data_cleaning.ipynb
```

### 4. Run all cells
- Go to **Kernel → Restart & Run All**
- Cleaned dataset will be saved to `data/cleaned_data.csv`

---

## 💡 Key Libraries Used

| Library | Purpose |
|---------|---------|
| `pandas` | Data loading, manipulation, cleaning |
| `numpy` | Numerical operations, IQR calculation |
| `matplotlib` | Charts and visualisations |
| `seaborn` | Heatmaps, distribution plots |

---

## 📸 Screenshots

### Missing Values Heatmap (Before Cleaning)
![Missing Values](screenshots/missing_values_heatmap.png)

### Data Quality Dashboard (After Cleaning)
![Cleaning Summary](screenshots/cleaning_summary_chart.png)

---

## 🔗 Connect

- **LinkedIn:** [linkedin.com/in/affan-inamdar-bb32a3342](https://linkedin.com/in/affan-inamdar-bb32a3342)
- **GitHub:** [github.com/affanazinamdar91](https://github.com/affanazinamdar91)
- **Email:** afaninamdar91@gmail.com

---

*Submitted as Task 1 — Data Science Internship*
