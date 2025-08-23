# 🛠️ Methodology – Customer Churn Analysis

This document explains the **approach and methods** used in the churn analysis project.

---

## 1. Data Preparation
- Imported dataset (`bank_churn.csv`) into **Power BI**.
- Cleaned missing values and ensured correct data types:
  - Converted `CreditScore` column to **numeric**.
  - Handled null/blank values in demographics.
- Created calculated columns using **Power Query** for better segmentation.

---

## 2. Data Transformation
### Credit Score Categorization
Defined ranges using **DAX SWITCH**:
- Poor: `< 500`
- Average: `500–650`
- Good: `651–800`
- Excellent: `> 800`

```DAX
CreditCategory =
SWITCH(
    TRUE(),
    Bank_Churn[CreditScore] < 500, "Poor",
    Bank_Churn[CreditScore] >= 500 && Bank_Churn[CreditScore] <= 650, "Average",
    Bank_Churn[CreditScore] >= 651 && Bank_Churn[CreditScore] <= 800, "Good",
    Bank_Churn[CreditScore] > 800, "Excellent",
    "Unknown"
)

