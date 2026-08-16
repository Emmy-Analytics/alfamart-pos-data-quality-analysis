# 📊 Alfamart POS Data Quality Analysis

**Capstone Project 3 – Purwadhika (Business Data Analyst) | Python | Pandas | Exploratory Data Analysis**

> An exploratory data analysis project focused on identifying POS data quality issues, promotional risks, and operational improvement opportunities from Alfamart transaction data.

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-blue?logo=pandas)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)
![Project](https://img.shields.io/badge/Project-Completed-success)
![EDA](https://img.shields.io/badge/Analysis-EDA-purple)

---

## 📌 Project Overview

This project was developed as **Capstone Project 3** for the Purwadhika Business Data Analyst program.

The analysis uses POS transaction data to investigate potential data quality problems and operational risks that may affect:

- Promotional effectiveness
- Cashier transaction accuracy
- Payment data consistency
- POS reporting reliability
- Transaction validation

The project combines transaction data with store and product master data to validate business rules and identify abnormal transaction patterns.

---

## 🎯 Business Problems

The analysis focuses on four main business areas:

### 1. Promo Protection

JSM transactions are analyzed to understand transaction volume and member identification.

A major limitation was identified because a significant portion of transactions does not contain `member_id`, making it difficult to identify repeat customers or potential bulk buyers.

### 2. Cashier SOP Evaluation

Transaction quantities are analyzed to identify unusual values that may indicate:

- Data-entry errors
- Scanning issues
- Returns or voids
- Transaction adjustments

### 3. Master Data Management

Payment method values contain inconsistent labels such as:

- `Cash`
- `CASH`
- `Tunai`
- `BCA Debit`
- `debit bca`
- `qris`
- `QRIS`

These values need to be standardized before reliable reporting and aggregation.

### 4. Fraud & System Error Detection

Transaction dates are compared with each store's official opening date to identify transactions that occurred before a store was officially opened.

---

## 🎯 Objectives

The objectives of this project are:

- Identify data quality issues in POS transaction records.
- Analyze abnormal transaction quantities.
- Evaluate missing customer identification.
- Standardize inconsistent payment method values.
- Validate transaction dates against store opening dates.
- Translate analytical findings into practical business recommendations.

---

## 🔍 Key Findings

### 👤 Missing Member ID

**120,000 transactions (40%)** have missing `member_id`.

For JSM transactions, **40.27%** do not have a member ID.

This limits member-level analysis and makes it difficult to determine whether unusual purchases are associated with repeat buyers or resellers.

---

### 🧾 Quantity Anomalies

The analysis identified:

- **1,483 transactions** with negative quantities.
- Maximum recorded quantity: **9,999 units**.
- **1,517 transactions** contain extreme quantities of 999 or 9,999 units.
- **Food & Staples** has the highest number of negative-quantity transactions.

These records require further investigation because they may represent returns, voids, adjustments, scanning errors, or data-entry issues.

---

### 💳 Payment Method Inconsistency

Payment method labels were standardized into six consistent categories:

- Cash
- BCA Debit
- QRIS
- Gopay
- ShopeePay
- OVO

The analysis identified **105,000 transactions (35%)** with inconsistent payment method labels before standardization.

Standardized values improve the reliability of aggregation, comparison, and reporting across stores.

---

### 🚨 Transaction Date Validation

**9,000 transactions** were recorded before the official opening dates of their stores.

This indicates potential logical errors in POS transaction records and highlights the need for system-level date validation.

---

## 💡 Business Recommendations

### 🎯 Promo Protection

1. Require customer identification for promotional transactions where appropriate.
2. Apply purchase-limit rules for JSM promotions.
3. Add a POS warning when promotional quantities exceed the allowed limit.

### 🧾 Cashier SOP Evaluation

1. Provide targeted cashier training based on abnormal quantity patterns.
2. Add a POS warning for unusually high quantities.
3. Require a reason code for negative quantities:
   - Void
   - Return
   - Adjustment

Example:

```text
⚠️ UNUSUAL QUANTITY

Entered quantity: 9,999 units

Please confirm the quantity.

[Re-scan]    [Confirm]
```

For negative quantities:

```text
⚠️ NEGATIVE QUANTITY

Quantity: -1

Reason:
○ Void
○ Return
○ Adjustment

[Submit]
```

### 💳 Master Data Management

1. Standardize payment method values across stores.
2. Replace free-text payment entry with a standardized POS dropdown.
3. Use consistent master-data values for reporting.

Example:

```text
PAYMENT METHOD

Select payment method:

▼ Cash

Cash
BCA Debit
QRIS
Gopay
ShopeePay
OVO

[Confirm Payment]
```

### 🚨 Fraud & System Error Detection

1. Add a POS date-validation rule.
2. Prevent transactions before the official store opening date.
3. Create an exception report for transactions that violate business rules.

Example:

```text
🚫 TRANSACTION BLOCKED

Store opening date: 15 Jul 2023
Transaction date: 10 Jul 2023

Transaction cannot be processed
before store opening.

[OK]
```

---

## 📁 Project Structure

```text
alfamart-pos-data-quality-analysis/
│
├── data/
│   └── README.md
│
├── images/
│   └── .gitkeep
│
├── Alfamart_POS_Data_Quality_Analysis.ipynb
├── README.md
├── requirements.txt
└── .gitignore
```

---

## 📓 Notebook

The complete analysis is available in:

**`Alfamart_POS_Data_Quality_Analysis.ipynb`**

The notebook contains:

- Data loading
- Data understanding
- Data preparation
- Data cleaning
- Data validation
- Exploratory Data Analysis
- Business analysis
- Key findings
- Business recommendations
- Conclusion

---

## 🔄 Analysis Flow

```text
Raw POS Data
      ↓
Data Understanding
      ↓
Data Preparation
      ↓
Data Cleaning & Validation
      ↓
Exploratory Data Analysis
      ↓
Business Problem Analysis
      ↓
Key Findings
      ↓
Business Recommendations
```

---

## 🛠️ Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- SciPy
- Jupyter Notebook
- VS Code
- Git & GitHub

---

## 🚀 How to Run

### Clone the repository

```bash
git clone https://github.com/Emmy-Analytics/alfamart-pos-data-quality-analysis.git

```

### Run the notebook

Open:

```text
POS TRANSACTION DATA ANALYSIS - ALFAMART STUDY CASE.ipynb
```

using Jupyter Notebook, JupyterLab, or VS Code.

---

## 📂 Dataset

The notebook expects these datasets:

```text
alfa_stores.csv
alfa_products.csv
alfa_pos_transactions.csv
```

The original CSV datasets are not included in this repository package because they were not provided with the notebook.

If the datasets contain confidential or restricted information, they should **not** be uploaded to a public GitHub repository.

---

## 🎯 Project Outcome

This project demonstrates how data quality analysis can be translated into practical business actions.

The main improvement opportunities identified are:

| Business Area | Opportunity |
|---|---|
| Promo Protection | Customer identification & purchase limits |
| Cashier SOP | Quantity validation & cashier training |
| Master Data | Standardized payment methods |
| POS Validation | Transaction-date validation |

The recommendations are designed to **support employees and improve operational controls**, rather than replace daily operational roles.

---

## 📝 Conclusion

The analysis highlights four key areas for business improvement:

- **Promo Protection:** Improve customer identification and promotional purchase controls.
- **Cashier SOP Evaluation:** Strengthen quantity validation and cashier procedures.
- **Master Data Management:** Standardize payment method input.
- **Fraud & System Error Detection:** Validate transaction dates against store opening dates.

Overall, the project demonstrates how data analysis can help transform raw POS data-quality issues into actionable operational improvements.

---

## 👩‍💻 Author

### Emmy Jacklyn Pontoan

**Aspiring Business Data Analyst**

Currently learning:

- 🐍 Python
- 🗄️ SQL
- 📊 Excel
- 📈 Business Analytics
- 📉 Data Visualization
- 🧹 Data Cleaning & EDA

---

⭐ Thank you for visiting this repository!
