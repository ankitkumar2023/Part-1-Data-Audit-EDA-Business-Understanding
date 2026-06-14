
# D2C Customer Churn Intelligence — Part 1: Data Audit, EDA & Business Understanding

## Project Overview

This repository contains Part 1 of the D2C Customer Churn Intelligence Capstone Project.

The objective of this phase is to perform a comprehensive audit of the raw business datasets, understand customer behavior patterns, identify possible churn drivers, and convert analytical findings into business recommendations.

This work serves as the foundation for future customer segmentation, churn prediction modeling, and retention strategy development.

---

## Business Problem

A direct-to-consumer personal-care brand wants to reduce customer churn intelligently rather than offering unnecessary discounts to all customers.

The analysis aims to answer the following questions:

* Which customer behaviors are associated with higher churn risk?
* Which customer segments require further investigation?
* Are there quality issues within the raw data that could impact business decisions?
* What signals should be considered before creating retention campaigns?

---

# Repository Structure

```
D2C-Churn-Intelligence-Part-1/
│
├── eda_audit.ipynb                 # Complete data loading, audit, EDA, and churn analysis notebook
│
├── data_quality_report.md          # Data quality findings and treatment recommendations
│
├── business_memo.md                # Business-focused churn investigation recommendations
│
├── requirements.txt                # Python libraries required to execute the notebook
│
├── churn_risk_hypotheses.csv       # Generated evidence of identified churn patterns
│
└── high_risk_customer_examples.csv # Customer-level examples requiring manual investigation
```

---

# Dataset Information

The analysis uses the following raw datasets:

* customers.csv
* orders.csv
* support_tickets.csv
* web_events_snapshot.csv
* churn_labels.csv
* intervention_history.csv

The datasets must be downloaded from the official Google Drive dataset package provided in the capstone instructions.

---

# Important Leakage Prevention Rule

The customer snapshot date is **2025-09-30**.

Orders occurring after this date represent future customer behavior and are intentionally excluded from all analytical calculations.

Only historical information available on or before the snapshot date is used for customer behavior analysis.

---

# How to Run This Repository in Google Colab

## Step 1: Clone the Repository

Open Google Colab and run:

```bash
!git clone <YOUR_PUBLIC_GITHUB_REPOSITORY_LINK>
```

---

## Step 2: Download Dataset into Google Drive

Create a folder inside your Google Drive:

```
MyDrive/
    D2C_Customer_Churn_Dataset/
```

Copy the following files into this folder:

* customers.csv
* orders.csv
* support_tickets.csv
* web_events_snapshot.csv
* churn_labels.csv
* intervention_history.csv

---

## Step 3: Open and Execute the Notebook

Open:

```
eda_audit.ipynb
```

The notebook automatically executes the following workflow:

1. Mounts Google Drive.
2. Loads all raw datasets.
3. Validates schemas and join relationships.
4. Detects missing values and duplicate records.
5. Removes post-snapshot order leakage.
6. Performs exploratory data analysis.
7. Generates customer churn hypotheses.
8. Exports customer evidence files.

---

# Key Analytical Areas Covered

The notebook evaluates:

* Customer demographics and acquisition channels.
* Purchase frequency and monetary behavior.
* Loyalty program participation.
* Product return patterns and ratings.
* Customer support experience.
* Website and application engagement.
* Previous campaign interactions.
* Churn distribution and customer risk signals.

---

# Output Files Generated

Running the notebook produces additional evidence files:

* `churn_risk_hypotheses.csv`
* `high_risk_customer_examples.csv`

These files provide business-ready evidence supporting retention investigations.

---

# Technology Stack

* Python 3.x
* Google Colab
* Pandas
* NumPy
* Matplotlib
* Seaborn

---

# Evaluation Checklist

This repository satisfies the Part 1 submission requirements:

✅ Complete data loading and schema inspection

✅ Data quality audit with treatment recommendations

✅ Leakage-safe historical customer analysis

✅ Multiple EDA charts and business visualizations

✅ Customer churn-risk hypothesis generation

✅ Business investigation memo

✅ Reproducible execution instructions

---

## Final Note

This repository is intentionally designed as a standalone submission.

An evaluator can understand the business objective, reproduce the analysis, review evidence, and continue to later capstone phases without requiring any additional repositories.
