# python-sales-eda
This repository contains a step-by-step Exploratory Data Analysis (EDA) performed on sales_data_sample.csv using Python, Pandas, NumPy and Matplotlib.
Here is a **clean, professional, GitHub-ready EDA description** that clearly explains every step performed.
You can paste this directly into your **README.md** or project documentation.

---

# 📊 Exploratory Data Analysis (EDA) – Sales Dataset

This repository contains a step-by-step Exploratory Data Analysis (EDA) performed on **sales_data_sample.csv** using **Python**, **Pandas**, **NumPy**, **Matplotlib**, and **Seaborn**.
The objective of the EDA is to clean, standardize, analyze, and visualize the dataset to make it ready for further analytics or modeling.

---

## 📁 1. Data Loading

* Loaded the dataset using `pandas.read_csv()`.
* Used `ISO-8859-1` encoding to resolve decoding errors caused by mixed character formats.

---

## 🧹 2. Column Name Cleaning

To ensure consistency and easier handling:

* Converted all column names to lowercase.
* Replaced spaces and special characters with underscores.
* Removed leading/trailing underscores.

Example:
`"ORDER NUMBER"` → `"ordernumber"`.

---

## 🔍 3. Initial Inspection

Performed the following:

* Checked dataset **shape** (rows, columns).
* Displayed column names.
* Viewed the first few rows with `df.head()`.
* Reviewed datatypes and null counts using `df.info()`.
* Generated summary statistics for numerical columns with `df.describe()`.

---

## ❓ 4. Missing Value Analysis

* Used `.isnull().sum()` to identify missing values.
* Displayed missing values in descending order.
* Handled missing values as follows:

  * **Numeric columns** → filled with **median**.
  * **Categorical columns** → filled with **mode** (most frequent value).
  * Converted `"nan"` strings to actual `NaN` values for proper handling.

---

## 🔁 5. Duplicate Removal

* Used `.duplicated()` to identify duplicates.
* Removed duplicates using `.drop_duplicates()` and reset index.

---

## 📝 6. Text Standardization

To ensure consistency:

* Converted all text-based columns to stripped lowercase strings.
* Standardized country names using mapping (e.g., `"usa"`, `"u.s.a"`, `"US"` → `"United States"`).
* Removed trailing periods, whitespace, and inconsistencies in categorical columns.

---

## 🗓️ 7. Date Column Fixing

The `orderdate` column contained inconsistent formats (e.g., `"2/24/2003 0:00"` and `"05-07-2003 00:00"`).

Approach:

1. Converted using `pd.to_datetime(..., dayfirst=False)`.
2. Re-attempted conversion for failed entries with `dayfirst=True`.
3. Replaced original column with cleaned datetime version.

---

## 🔢 8. Data Type Corrections

Some numeric-like columns were incorrectly stored as strings.

Converted these to numeric types:

* `ordernumber`
* `quantityordered`
* `priceeach`
* `sales`
* `qtr_id`
* `month_id`
* `year_id`

Used:

```python
df[col] = pd.to_numeric(df[col], errors="coerce")
```

Converted appropriate columns to integer dtype (`Int64`).

---

## 📉 9. Exploratory Visualizations

Using **Matplotlib** (as per tool constraints):

### **a) Top 10 Countries by Total Sales (Bar Chart)**

* Grouped by `country` and summed `sales`.
* Visualized top 10 countries.

### **b) Distribution of Quantity Ordered (Histogram)**

* Helped identify demand patterns and frequency.

### **c) Boxplot of Price Each**

* Identified outliers and price variability.

---

## 💾 10. Saving the Cleaned Dataset

Exported the cleaned dataset as:

```
sales_data_sample_cleaned.csv
```

Ready for further BI dashboards, modeling, or reporting.

---

# Summary

This EDA:

* Cleaned and standardized the dataset.
* Resolved missing values and inconsistencies.
* Fixed datatypes and standardized text columns.
* Converted date formats.
* Produced key visual insights.
* Prepared a **clean, analysis-ready dataset**.

---
