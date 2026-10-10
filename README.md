📊 Sales Analytics Case Study
End-to-End Data Analytics Project

Data Science Internship — SWYNEX Technologies Author: Affan Inamdar | Year: 2026

Python Power BI Pandas

📌 Project Overview

This is a complete end-to-end data analytics case study performed on a Global Sales Dataset covering 2,823 transactions across 19 countries from 2003 to 2005. The project covers the full analytics pipeline:

Raw Data → Data Cleaning → EDA → Interactive Dashboard → Business Insights
✅ Tasks Completed
Task	Description	Status	Key Output
Task 1	Data Cleaning & Preparation	✅ Complete	cleaned_data.csv
Task 2	Exploratory Data Analysis	✅ Complete	8 EDA Charts
Task 3	Interactive Power BI Dashboard	✅ Complete	.pbix Dashboard
Final	Complete Analytics Case Study	✅ Complete	CASE_STUDY.md
🎯 Problem Statement

A global B2B sales company needed to understand:

Which product lines and territories drive the most revenue?
Who are the most valuable customers?
What are the seasonal sales trends?
How can order completion rates be improved?
📊 Dataset
Property	Value
Records	2,823 rows × 25 columns
Time Period	Jan 2003 — May 2005
Countries	19
Customers	92
Products	109
Total Revenue	$9,934,834
💡 Key Business Insights
#	Insight	Finding
1	Geographic concentration	EMEA = 88% of revenue
2	Product concentration	Classic Cars = 39% of revenue
3	Customer concentration	Top 2 customers = 15.5% revenue
4	Revenue growth	2004 peak year — +34% vs 2003
5	Operations	92.7% order completion rate
6	Deal segments	Medium deals = 61% of revenue
7	Pricing impact	Strong correlation: price vs sales
📁 Repository Structure
data-cleaning-task/
│
├── raw_data.csv                      ← Original dataset
├── cleaned_data.csv                  ← Cleaned output (Task 1)
├── data_cleaning.ipynb               ← Task 1: Cleaning notebook
├── eda_analysis_FIXED.ipynb          ← Task 2: EDA notebook
├── Sales_Analytics_Dashboard.pbix    ← Task 3: Power BI file
├── Sales_Analytics_Dashboard.pdf     ← Task 3: PDF export
├── CASE_STUDY.md                     ← Full case study document
├── README.md                         ← This file
│
└── Screenshots/
    ├── Task 1 screenshots (12 files)
    ├── Task 2 EDA charts (8 files)
    └── Task 3 dashboard (2 files)
🧹 Task 1 — Data Cleaning

Issues Fixed:

Issue	Action
Missing values	Median (numeric) + Mode (categorical)
Duplicates	Removed, kept first
Wrong data types	pd.to_datetime() conversion
Inconsistent text	str.strip() + str.title()
Outliers	IQR capping (Winsorization)
Derived columns	Added Year, Month, Quarter

Screenshots:

Show Image Show Image

🔍 Task 2 — Exploratory Data Analysis

7 insights extracted across 8 professional charts.

Show Image Show Image Show Image

📈 Task 3 — Power BI Dashboard

2-page interactive dashboard with 5 slicers and 8 DAX measures.

Show Image Show Image

✅ Recommendations
Expand into APAC & Japan — only 12% of current revenue
Diversify product portfolio — reduce Classic Cars dependency
Acquire new customers — reduce top-2 customer concentration risk
Plan for Q4 peak — revenue spikes every Q4
Investigate cancellations — 60 cancelled orders = lost revenue
Focus on USA market — $3.59M potential to grow further
Retain medium deal customers — 61% of total revenue
🛠️ How to Run
bash
# Install dependencies
pip install pandas numpy matplotlib seaborn jupyter

# Task 1 — Data Cleaning
jupyter notebook data_cleaning.ipynb

# Task 2 — EDA
jupyter notebook eda_analysis_FIXED.ipynb

# Task 3 — Open in Power BI Desktop
# File: Sales_Analytics_Dashboard.pbix
💻 Tech Stack

Python · Pandas · NumPy · Matplotlib · Seaborn · Jupyter · Power BI · DAX · Git

🔗 Connect
LinkedIn: linkedin.com/in/affan-inamdar-bb32a3342
GitHub: github.com/affanazinamdar91
Email: afaninamdar91@gmail.com

Final Project — Data Science Internship @ SWYNEX Technologies | Affan Inamdar | 2026
