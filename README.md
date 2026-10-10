# Internship Progress - Day 24: Data Type Cleaning
**AI & ML Track | Level 1**

## 📌 Task Overview
This project focuses on identifying incorrect data types in a dataset and converting columns to their appropriate data types using Python and Pandas. Proper data typing is a foundational step in exploratory data analysis (EDA) and machine learning preprocessing.

---

## 🛠️ Tools Used
* **Python**
* **Pandas**
* **Jupyter Notebook**

---

## 🎯 Deliverables Included
1. **Original Data Types:** Inspection of raw/dirty data types (`df.dtypes`).
2. **Corrected Data Types:** Cleaned data types after applying transformation functions (`astype`, `pd.to_numeric`, `pd.to_datetime`, and mapping).
3. **Explanation of Conversions:** Detailed rationale for why each data type adjustment was required.

---

## 📝 Implementation Code (Jupyter Notebook / Python Script)

```python
import pandas as pd

# 1. Simulating the dataset for demonstration purposes
data = {
    'employee_id': ['101', '102', '103', '104'],
    'salary': ['50000', '65000.50', 'not_available', '72000'],
    'joining_date': ['2022-01-15', '2022-05-20', '2023-01-10', '2023-03-01'],
    'is_active': ['True', 'False', 'True', 'True']
}
df = pd.DataFrame(data)

# DELIVERABLE 1: Original Data Types
print("=== 1. ORIGINAL DATA TYPES ===")
print(df.dtypes)
print("\nDataFrame Preview:")
print(df)

print("\n" + "="*40 + "\n")

# 2. Cleaning and converting data types
df['employee_id'] = df['employee_id'].astype(int)

# Using errors='coerce' turns invalid parsing (like 'not_available') into NaN
df['salary'] = pd.to_numeric(df['salary'], errors='coerce')

df['joining_date'] = pd.to_datetime(df['joining_date'])

# Map boolean strings safely
df['is_active'] = df['is_active'].map({'True': True, 'False': False})

# DELIVERABLE 2: Corrected Data Types
print("=== 2. CORRECTED DATA TYPES ===")
print(df.dtypes)
print("\nCleaned DataFrame:")
print(df)