# Buyer Payment Risk & Fraud Analytics

<img width="1403" height="787" alt="image" src="https://github.com/user-attachments/assets/d44fdef3-9ec8-488a-ae00-d9e563f6fe16" />


This project analyzes synthetic e-commerce payment transaction data to identify fraud patterns, risk drivers, customer friction, and operational investigation trends.

The project was designed as a portfolio case study for a Risk Analyst / Business Analyst role involving payment risk, fraud prevention, SQL analysis, Python, and Power BI.

The analysis focuses on answering key business questions:

- What is the overall fraud rate and fraud exposure?
- Which payment methods show higher fraud risk?
- Which risk levels and risk signals are most associated with fraud?
- Does combining multiple risk signals improve fraud detection?
- Does transaction velocity indicate elevated fraud risk?
- Are newer customer accounts associated with higher fraud risk?
- Which devices require enhanced monitoring?
- What customer friction events are occurring?
- How are fraud investigations distributed by severity and status?

---

## Important Data Note

The dataset used in this project is **synthetic** and was created specifically for portfolio analysis.

It does not contain Amazon, customer, payment, or proprietary company data.

The dataset was designed to simulate a realistic e-commerce payment-risk environment while keeping the analysis suitable for public portfolio use.

---

## Tools & Technologies

- **SQL / MySQL** - Data validation, joins, aggregation, fraud analysis and risk segmentation
- **Power BI** - Data modeling, DAX, dashboards and business visualization
- **Python** - Data analysis and supporting data preparation
- **Excel** - Supporting data inspection and validation

---

## Dataset

The synthetic dataset contains the following tables:

| Table | Description |
|---|---|
| customers | Customer profile and account information |
| payment_methods | Payment method reference data |
| devices | Device information |
| transactions | Core transaction-level data |
| transaction_risk_signals | Transaction-level fraud risk indicators |
| fraud_cases | Fraud investigation and case management data |
| customer_friction | Customer friction and payment-related events |

Dataset size:

- 50,000 customers
- 500,000 transactions
- 500,000 transaction risk records
- 12,486 fraud cases
- 35,017 customer friction events

---

# Business Analysis

## 1. Overall Fraud & Payment Risk

Key metrics:

| Metric | Result |
|---|---:|
| Total Transactions | 500,000 |
| Fraud Transactions | 12,486 |
| Fraud Rate | 2.50% |
| Fraud Transaction Value | 10.29M |
| Average Transaction Value | $707.65 |

The overall fraud rate provides the baseline against which individual risk segments and signals are evaluated.

---

## 2. Fraud Risk by Payment Method

Payment methods with the highest fraud rates:

| Payment Method | Fraud Rate |
|---|---:|
| PayPal | 3.71% |
| Buy Now Pay Later | 3.39% |
| Net Banking | 2.50% |
| Credit Card | 2.41% |
| Gift Card | 2.40% |
| Debit Card | 2.39% |
| Digital Wallet | 2.35% |
| UPI | 2.31% |

PayPal and Buy Now Pay Later show the highest fraud rates in the dataset.

However, payment method alone should not automatically be treated as a reason to block transactions. Additional behavioral and transactional signals should be considered.

---

## 3. Fraud Rate by Risk Level

| Risk Level | Fraud Rate |
|---|---:|
| High | 8.02% |
| Medium | 5.37% |
| Low | 2.17% |
| Critical | 0.00% |

The High-risk segment has a materially higher fraud rate than the overall 2.50% baseline.

The Critical segment contains only a very small number of transactions, so its result should be treated as directional rather than statistically representative.

---

## 4. Risk Signal Analysis

Individual risk signals were evaluated based on the fraud rate of transactions carrying each signal.

| Risk Signal | Fraud Rate |
|---|---:|
| Previous Chargeback | 5.50% |
| High Value | 5.43% |
| New Account | 5.02% |
| Multiple Payment Failures | 4.13% |
| High Velocity | 3.88% |
| Unusual Location | 2.49% |

Previous chargeback, high-value activity, and new-account activity are the strongest individual indicators in this dataset.

Unusual location has a fraud rate close to the overall baseline, indicating limited standalone discrimination.

---

## 5. Combined Risk Signals

Fraud rate increases as multiple risk signals are present:

| Risk Signal Count | Fraud Rate |
|---|---:|
| 0 | 1.55% |
| 1 | 3.65% |
| 2 | 5.87% |
| 3 | 7.43% |
| 4 | 8.57% |
| 5 | 25.00% |

Transactions with multiple risk indicators show substantially higher fraud rates than transactions with no risk signals.

This supports prioritizing combinations of risk indicators rather than treating every signal independently.

---

## 6. Transaction Velocity

| Velocity Band | Fraud Rate |
|---|---:|
| Low Velocity | 2.32% |
| Medium Velocity | 2.34% |
| High Velocity | 3.88% |
| Very High Velocity | 3.13% |

High transaction velocity shows an elevated fraud rate compared with the overall baseline.

The Very High Velocity segment contains a small number of transactions and should therefore be interpreted cautiously.

---

## 7. Account Age Analysis

| Account Age | Fraud Rate |
|---|---:|
| 0-7 Days | 5.00% |
| 8-30 Days | 5.20% |
| 31-90 Days | 1.94% |
| 91-365 Days | 2.09% |
| 366+ Days | 2.06% |

Newer customer accounts show higher fraud rates in this synthetic dataset.

This suggests that account age can be useful as one component of a broader risk assessment framework.

---

## 8. Device Risk

A focused analysis of the highest-risk devices identified a small group of devices with elevated fraud rates.

The selected top-risk device group contained:

- 274 transactions
- 69 fraud transactions
- 25.18% fraud rate
- $200K+ transaction value

Because this is a relatively small segment, these devices should be considered for enhanced monitoring or investigation rather than automatic blocking.

---

## 9. Customer Friction

Customer friction events were analyzed to understand whether common friction types independently indicate fraud.

The major friction categories were:

- Payment Decline
- Verification Required
- Repeated Payment Attempt
- Account Review

Fraud rates across these friction categories were close to the overall baseline.

This suggests that customer friction alone is not a strong standalone fraud discriminator and should be combined with stronger transactional and behavioral signals.

---

# Power BI Dashboard

The Power BI report contains three pages.

## Page 1 - Buyer Payment Risk & Fraud Analytics

Executive risk overview containing:

- Total Transactions
- Fraud Transactions
- Fraud Rate
- Fraud Value
- Average Transaction Value
- Fraud Rate by Payment Method
- Fraud Value by Payment Method
- Fraud Rate by Risk Level
- Fraud Rate by Number of Risk Signals
- Transactions Distribution by Fraud Flag
- Payment Method, Payment Status and Velocity Band filters
- Key Risk Takeaways

## Page 2 - Risk Drivers & Behavioral Analysis

Contains:

- Fraud Rate by Risk Signal
- Fraud Rate by Transaction Velocity
- Fraud Rate by Device Type
- Fraud Rate by Account Age

## Page 3 - Fraud Investigation & Case Management

Contains:

- Fraud Cases by Severity
- Fraud Cases by Investigation Status
- Average Resolution Time by Severity
- Customer Friction Events by Type

---

# Key Business Insights

### 1. Multiple risk signals matter

Transactions carrying multiple risk indicators show materially higher fraud rates than transactions with no risk signals.

### 2. Previous chargebacks are a strong indicator

Previous chargeback activity has the highest individual fraud rate among the evaluated signals.

### 3. High transaction velocity requires attention

High-velocity transactions show elevated fraud risk and can be considered for enhanced monitoring.

### 4. New accounts show higher risk

Accounts in the early stages of their lifecycle have higher observed fraud rates in this synthetic dataset.

### 5. Customer friction should not automatically equal fraud

Payment declines, verification requests and other friction events are common and are not highly discriminatory on their own.

### 6. Risk controls should combine signals

A practical fraud-prevention approach should combine transaction characteristics, customer behavior, payment information, velocity and historical risk indicators rather than relying on a single signal.

---

# Data Quality Validation

Before analysis, the dataset was validated for:

- Duplicate transaction IDs
- Invalid customer references
- Invalid payment method references
- Invalid device references
- Orphan risk signals
- Orphan fraud cases
- Orphan customer friction records
- Invalid transaction amounts
- Invalid fraud flags
- Invalid risk scores

All validation checks returned zero exceptions.

---

# Project Outcome

This project demonstrates an end-to-end analytics workflow:

**Raw Data → Data Validation → SQL Analysis → Risk Segmentation → Power BI Data Model → DAX Measures → Dashboard → Business Insights**

The project demonstrates practical skills in:

- SQL
- Relational data modeling
- Data quality validation
- Fraud and risk analysis
- Risk segmentation
- KPI development
- DAX
- Power BI dashboard development
- Business storytelling
- Actionable insight generation
