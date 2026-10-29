# Telco Customer Churn Analysis

**Project charter.** Written retrospectively in October 2026 from the project's phase records, when the project was brought in line with the Data Analysis Playbook v3.4. The analysis itself was carried out in July 2026. This document records the question, scope and definitions the analysis used; it was not written before the data was examined, and nothing in it should be read as a rule set in advance.

---

# Project Overview

| Item | Details |
|------|---------|
| Project | 7 of the portfolio |
| Domain | CRM / customer analytics |
| Type | Descriptive churn and revenue analysis |
| Tools | MySQL Workbench (computation), Microsoft Excel with Power Query (reporting) |
| Author | Taofeek Salami |
| Analysis period | July 2026 |
| Status | Complete; revised October 2026 (see README → Corrections) |

---

# Business Context

A subscription telecom company bills customers monthly on month-to-month, one-year or two-year contracts. Customers who leave take their monthly charges with them. The business wants to know where churn is concentrated so it can decide where retention effort should go.

This is a portfolio project on public IBM sample data. The stakeholders below are modelled on a typical subscription business.

---

# Business Problem

Churn is visible as a single overall rate, but the business does not know which customer groups churn most, how much recurring revenue churned customers accounted for, or how much of its remaining revenue depends on high-churn groups.

---

# Primary Business Question

Which customer groups have the highest churn, how much monthly revenue did churned customers account for, and how concentrated is revenue in those groups?

---

# Supporting Analytical Questions

1. What is the overall churn rate?
2. How does the churn rate differ by contract type, tenure, internet service and payment method?
3. What monthly and annualised charges were paid by customers who churned, and what share of all monthly charges is that?
4. How do average charges, revenue per customer and estimated lifetime value differ by contract and churn status?
5. What share of customers and of monthly revenue sits in each contract type and internet service?
6. Which combination of contract, charges and tenure has the highest churn rate?

---

# Stakeholders (modelled)

| Stakeholder | Interest |
|-------------|----------|
| Customer retention / customer success | Which customers to focus on |
| Finance | Revenue paid by churned customers and revenue concentration |
| Product and network teams | Whether a service (fibre optic) stands out |
| Leadership | Structural exposure of revenue to high-churn groups |

---

# Scope

## Included

- Churn rates, customer shares and revenue shares by contract, tenure band, internet service, payment method and charge tier
- Monthly charges of churned customers, annualised
- Average revenue per customer and a simple lifetime value estimate by contract and churn status
- One rule-based profile (month-to-month, over £70 a month, under 12 months' tenure)

## Excluded

- Statistical significance testing of the differences between groups
- Predictive modelling or scoring of individual customers
- Causes of churn, which the data cannot show
- Any analysis over time, since the data has no dates

---

# Available Data

IBM Telco Customer Churn sample data from Kaggle (`blastchar/telco-customer-churn`), file `WA_Fn-UseC_-Telco-Customer-Churn.csv`: 7,043 customers and 21 columns, one row per customer, with no dates. 11 early-tenure customers have a blank `TotalCharges`; these were set to NULL and no rows were removed. The checksum was not recorded at download.

---

# Metric Definitions

Every metric is computed in SQL (`sql/`) and exported to `data/`. The unit of analysis is one customer.

| Metric | Calculation | Denominator | Time window | Units |
|--------|-------------|-------------|-------------|-------|
| Churn rate | Customers with `Churn = 'Yes'` ÷ customers | Customers in the group | Status at the snapshot | % of customers |
| Share of churners | Churned customers in the group ÷ all churned customers | All 1,869 churned customers | Snapshot | % of churners |
| Customer share | Customers in the group ÷ all customers | All 7,043 customers | Snapshot | % of customers |
| Monthly revenue lost to churn | Sum of `MonthlyCharges` for churned customers | — | One month, at the snapshot | £ per month |
| Share of monthly charges lost | Monthly revenue lost ÷ all monthly charges | All customers' monthly charges | One month | % of monthly charges (a share, not a rate) |
| Annualised revenue lost | Monthly revenue lost × 12 | — | Twelve months | £ per year. Annualises a snapshot; not a forecast |
| Revenue share | Group's monthly charges ÷ all monthly charges | All customers' monthly charges | One month | % of monthly revenue |
| Average revenue per customer | Sum of `TotalCharges` ÷ customers | Customers with a recorded `TotalCharges` (excludes the 11 blanks) | Each customer's whole tenure | £ |
| Estimated lifetime value | Average tenure × average monthly charge, by contract and churn status | Customers in the group | Whole tenure | £. A rough group-level estimate, not a customer-level model |

**Group definitions.** Tenure bands: 0–12 months (tenure 0 to 12 inclusive, described as the first year), 13–36 months, 37+ months. Charge tiers: low (under £35), mid (£35 to under £70), high (£70 or more). High-risk profile: month-to-month contract, `MonthlyCharges` over £70 and tenure under 12 months.

**Currency.** The source data does not state a currency. Amounts are reported in pounds (£) for this project.

---

# Known Risks

| Risk | Effect | How it was handled |
|------|--------|--------------------|
| Overlapping groups | Contract, tenure, service and payment are related, so a high churn rate in one may reflect another | Reported as associations only; testing them together is listed as next work |
| Outcome-defined profile | The high-risk profile was found by looking at who churned, so it fits past churn by design | Described as where churn happened; recommended to test it on active customers before use |
| Snapshot data | No dates, so no trends, cohorts or causes | Stated in every summary; time-based analysis listed as next work |
| Unstated currency | Amounts could be misread | Currency note in the README, data dictionary and summaries |

---

# Assumptions

| Assumption | Status | Note |
|------------|--------|------|
| `Churn = 'Yes'` means the customer had left by the time of the snapshot | Not testable | Taken from the dataset description |
| `MonthlyCharges` is the amount billed per month at the snapshot | Not testable | Taken from the dataset description |
| Blank `TotalCharges` belong to new customers with no completed billing period | Partially validated | The Phase 0 record notes they are early-tenure customers; their exact tenure was not saved in a query ([phase_00_setup.md](docs/phase_00_setup.md)) |
| The 7,043 rows are distinct customers | Validated | The duplicate check returned no repeated customer IDs ([phase_01_sql.md](docs/phase_01_sql.md), query 2) |

---

# Deliverables

- 22 SQL queries in six scripts, and 17 CSV outputs
- Excel workbook with Power Query data layer, a 10-KPI framework and four dashboards
- Executive summary, data dictionary, eleven phase records and the project page

---

# Revision History

| Date | Change |
|------|--------|
| July 2026 | Analysis, workbook, dashboards and documentation completed |
| 26 Oct 2026 | Churn share, revenue-lost wording and high-risk claims corrected after the portfolio audit |
| 29 Oct 2026 | Workbook data errors fixed (swapped contract shares, mislinked KPI card); dashboard wording corrected; this charter written retrospectively; README restructured to the playbook v3.4 layout |
