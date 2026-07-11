# Phase 2 — Excel Data Model & Validation

**Tool:** Microsoft Excel (Mac)
**Workbook:** `Telco_Churn_Analysis.xlsx`
**Sheets Created:** 25 (Main Dashboard + 3 Supporting Dashboard + KPI_Framework + 20 data sheets)
**Tables Created:** 24
**Status:** Complete ✅

---

## Objective

Import SQL-exported CSVs into Excel as structured tables, validate data integrity, apply consistent formatting, and organise the workbook for analysis and dashboard development.

---

## Steps Completed

### Step 1 — Workbook Created

- New Excel workbook created and saved as `Telco_Churn_Analysis.xlsx`
- Stored within project folder: `project-7-telco-churn/`
- Default sheet renamed to `Dashboard` and set as the opening view

---

### Step 2 — CSV Import Method

- Method: Data → Get Data → From Text/CSV
- Each CSV imported into a dedicated sheet
- All datasets loaded as Excel Tables for structured referencing
- Sheet names and table names assigned immediately after import

---

### Step 3 — Tables Imported

| # | Sheet Name | Table Name | Rows |
|---|---|---|---|
| 1 | churn_by_contract | tbl_ChurnByContract | 3 |
| 2 | churn_by_tenure_band | tbl_ChurnByTenureBand | 3 |
| 3 | churn_by_internet_service | tbl_ChurnByInternetService | 3 |
| 4 | avg_tenure_by_churn | tbl_AvgTenureByChurn | 2 |
| 5 | churn_by_payment_method | tbl_ChurnByPaymentMethod | 4 |
| 6 | avg_charges_by_churn | tbl_AvgChargesByChurn | 2 |
| 7 | revenue_at_risk | tbl_RevenueAtRisk | 1 |
| 8 | revenue_by_contract | tbl_RevenueByContract | 3 |
| 9 | revenue_tiers | tbl_RevenueTiers | 3 |
| 10 | cumulative_revenue_by_tenure | tbl_CumulativeRevenue | 72 |
| 11 | concentration_risk | tbl_ConcentrationRisk | 3 |
| 12 | internet_service_concentration | tbl_InternetServiceConc | 3 |
| 13 | high_risk_customers | tbl_HighRiskCustomers | 2 |
| 14 | multi_dimension_churn | tbl_MultiDimensionChurn | 10 |
| 15 | estimated_ltv | tbl_EstimatedLTV | 6 |
| 16 | cohort_lag_analysis | tbl_CohortLagAnalysis | 5 |
| 17 | perfect_storm_churn | tbl_PerfectStormChurn | 3 |

---

### Step 4 — Validation

All tables validated against SQL outputs:

| Check | Result |
|---|---|
| Row counts match SQL output | ✅ All tables verified |
| Column names imported correctly | ✅ |
| No import errors detected | ✅ |
| Numeric columns correctly typed | ✅ |
| All tables populated | ✅ |

**Validation Verdict:** All datasets imported successfully with no inconsistencies detected.

---

### Step 5 — Column Standardisation

Column headers renamed across all tables for clarity and consistency.

**Naming conventions applied:**

- Segments: `Contract`, `Tenure Band`, `Revenue Tier`, `Internet Service`, `Payment Method`
- Volume: `Total Customers`, `Churned`
- Rates: `Churn Rate (%)`, `Revenue Share (%)`, `Customer Share (%)`
- Monetary: `Monthly Revenue (£)`, `Total Revenue (£)`, `Avg Monthly Charge (£)`, `Estimated LTV (£)`
- Comparison: `Churn Status`, `Avg Tenure (Months)`, `Change (pp)`

---

### Step 6 — Number Formatting

**Monetary columns**
- Format: Number (2 decimal places, comma separator)
- Currency symbol placed in column header, not cells

**Percentage columns**
- Format: Number (2 decimal places)
- `%` symbol placed in header

**Integer columns**
- Format: Number (0 decimal places, comma separator)

---

### Step 7 — Sheet Organisation

Workbook structured by analytical pillar:

1. Dashboard
2. Dashboard_Customer
3. Dashboard_Revenue
4. Dashboard_Risk
5. KPI_Framework

— Customer —

6. Churn_Analysis
7. churn_by_contract
8. churn_by_tenure_band
9. churn_by_internet_service
10. churn_by_payment_method
11. avg_tenure_by_churn 

— Revenue —

12. Revenue_Stability
13. avg_charges_by_churn
14. revenue_at_risk
15. revenue_by_contract
16. revenue_tiers
17. cumulative_revenue_by_tenure 

— Risk —

18. Segment_Risk
19. concentration_risk
20. internet_service_concentration
21. high_risk_customers

— Advanced (supporting analysis) —

22. multi_dimension_churn
23. estimated_ltv
24. cohort_lag_analysis
25. perfect_storm_churn

---

## Structural Notes

- SQL outputs are treated as the **single source of truth**
- Excel is used for:
  - Structuring insights
  - Combining datasets
  - Dashboard presentation
- Core metrics (churn rate, revenue, aggregates) are **not recalculated in Excel**

---

## Planned Next Layer (Phase 4–6)

Intermediate analysis will be created:

- `Churn_Analysis`
- `Revenue_Stability`
- `Segment_Risk`

These will:

- Combine multiple SQL tables
- Support KPI calculation and dashboard visuals
- Avoid duplication of SQL logic

---

## Validation Summary

| Check | Result |
|---|---|
| All CSVs imported | ✅ |
| All row counts verified | ✅ |
| Tables structured correctly | ✅ |
| Column naming standardised | ✅ |
| Formatting applied | ✅ |
| Workbook organised | ✅ |
| Ready for analysis | ✅ |

---

## Notes

- Some tables (e.g. cohort and advanced outputs) serve as **supporting analysis** and may not be used directly in the dashboard
- Raw CSV files remain unchanged in `/data` for traceability
- Excel (Mac) limitations (e.g. Distinct Count) will be handled using helper methods if required

---

**Status:** Phase 2 complete — structured Excel environment ready for KPI design and analysis.  
*Project 7: Telco Customer Churn Analysis — Framework: Customer · Revenue · Risk*
