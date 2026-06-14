
# D2C Customer Churn Intelligence — Data Quality Audit Report

## 1. Objective

The objective of this audit was to assess raw customer, transaction, support, web activity, campaign, and churn datasets before performing customer behavior analysis and developing future churn prediction models.

---

## 2. Dataset Coverage

The audit covered the following raw data sources:

* Customer profile data
* Order transaction history
* Customer support tickets
* Website and application activity
* Retention campaign history
* Churn labels

All datasets were validated using `customer_id` as the primary business key.

---

## 3. Missing Data Assessment

### Customer Dataset

| Column       | Issue                  | Business Interpretation                                  | Recommendation                                                          |
| ------------ | ---------------------- | -------------------------------------------------------- | ----------------------------------------------------------------------- |
| loyalty_tier | Missing values present | Customer is not enrolled in the loyalty program          | Convert missing values into a separate "No Loyalty Membership" category |
| skin_type    | Missing values present | Customer did not provide personal preference information | Keep missing values as "Unknown" instead of arbitrary imputation        |

---

### Order Dataset

| Column | Issue                    | Business Interpretation                                  | Recommendation                                                                         |
| ------ | ------------------------ | -------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| rating | Missing customer ratings | Customers completed purchases without providing feedback | Preserve null values during aggregation and calculate averages using available ratings |

---

## 4. Duplicate and Duplicate-Like Records

The orders dataset contains duplicate-like transaction identifiers ending with `_DUP`.

These records represent intentional data-quality challenges and should be investigated before creating production-grade financial or customer lifetime value metrics.

Recommended actions:

* Quantify duplicate impact on revenue calculations.
* Establish business rules for identifying true duplicate transactions.
* Remove confirmed duplicate records only after stakeholder validation.

---

## 5. Data Leakage Risk Assessment

The most critical modeling risk exists within the orders dataset.

Orders recorded after the customer snapshot date of `2025-09-30` represent future customer behavior and must not be used as predictive features.

These records should only be used to explain how churn labels were created.

All behavioral analysis and future modeling should use only historical information available before the snapshot date.

---

## 6. Outlier Assessment

Order value analysis identified unusually large purchase amounts.

Potential explanations include:

* Bulk purchases
* Premium product bundles
* Data entry anomalies
* High-value customers

Outliers should not be removed automatically because they may represent legitimate high-value customers.

Recommended treatment:

* Investigate extreme customers individually.
* Use robust statistics such as medians and percentiles.
* Apply capping only if business validation confirms anomalies.

---

## 7. Join Integrity Validation

All business datasets were validated using left joins from the customer master table.

Customers without support tickets or recent interactions were treated as legitimate business scenarios rather than missing data problems.

---

## 8. Final Data Quality Conclusion

The overall data quality is suitable for exploratory analysis and future machine-learning development.

However, the following controls must remain in place:

1. Prevent post-snapshot information leakage.
2. Monitor duplicate-like order records.
3. Preserve meaningful missing values as business signals.
4. Investigate extreme monetary transactions before production modeling.

Following these recommendations will ensure trustworthy churn insights and reliable downstream retention strategies.
