# Phase 5 — Revenue Stability Analysis

**Tool:** Microsoft Excel (Mac)  
**Sheet:** `Revenue_Stability`  
**Tables:** `tbl_RevenueByContractAnalysis` · `tbl_RevenueByTierAnalysis` · `tbl_EstimatedLTVAnalysis`  
**Charts Built:** 3  
**Status:** Complete ✅

---

## Objective

Build the Revenue pillar analytical layer combining revenue at risk, revenue by contract type, revenue by tier and estimated lifetime value into a structured, presentation-ready sheet. This sheet feeds `Dashboard_Revenue` and contributes the revenue story to the Executive Summary Dashboard.

---

## Sheet Structure

### Section 1 — Revenue at Risk Summary Block

A plain formatted reference block — not a table. Sits at the top of the sheet as the headline revenue finding.

| Label | Value | Source |
|---|---|---|
| Monthly Revenue Lost (£) | 139,130.85 | `=revenue_at_risk!A2` |
| Monthly Revenue Retained (£) | 316,985.75 | `=revenue_at_risk!B2` |
| Total Monthly Charges (£) | 456,116.60 | `=revenue_at_risk!C2` |
| Revenue at Risk (%) | 30.50 | `=revenue_at_risk!D2` |
| Annualised Revenue at Risk (£) | 1,669,570.20 | `=revenue_at_risk!A2*12` |

**Design:** Dark Navy header row, Annualised Revenue at Risk value in Bold Red `#C00000` — most impactful number on the sheet.

---

### Section 2 — Revenue by Contract Type

**Table:** `tbl_RevenueByContractAnalysis`
**Source:** `tbl_RevenueByContract` (revenue_by_contract sheet)

| Pillar | Segment Type | Segment | Total Revenue (£) | Avg Revenue per Customer (£) | Avg Monthly Charge (£) |
|---|---|---|---|---|---|
| Revenue | Contract | Two year | 6,283,253.70 | 3,728.93 | 60.87 |
| Revenue | Contract | Month-to-month | 5,305,861.50 | 1,369.25 | 66.40 |
| Revenue | Contract | One year | 4,467,053.50 | 3,034.68 | 65.08 |

**Row formatting:**
- Two year: Light Navy `#DAE3F3` — highest revenue per customer
- Month-to-month: Light Red `#FADBD8` — highest churn risk
- One year: White `#FFFFFF`

---

### Section 3 — Revenue by Tier

**Table:** `tbl_RevenueByTierAnalysis`
**Source:** `tbl_RevenueTiers` (revenue_tiers sheet)

| Pillar | Segment Type | Revenue Tier | Total Customers | Churned | Churn Rate (%) | Avg Monthly Charge (£) |
|---|---|---|---|---|---|---|
| Revenue | Revenue Tier | High value | 3,591 | 1,274 | 35.48 | 90.19 |
| Revenue | Revenue Tier | Mid value | 1,721 | 407 | 23.65 | 54.72 |
| Revenue | Revenue Tier | Low value | 1,731 | 188 | 10.86 | 22.00 |

**Row formatting:**
- High value: Light Red `#FADBD8` — highest churn rate
- Mid value: Light Gold `#FDF2D0`
- Low value: Light Navy `#DAE3F3` — lowest churn rate

---

### Section 4 — Estimated LTV

**Table:** `tbl_EstimatedLTVAnalysis`
**Source:** `tbl_EstimatedLTV` (estimated_ltv sheet)

| Pillar | Contract | Churn Status | Avg Tenure (Months) | Avg Monthly Charge (£) | Estimated LTV (£) |
|---|---|---|---|---|---|
| Revenue | Two year | Yes | 61.3 | 86.78 | 5,316.90 |
| Revenue | One year | Yes | 45.0 | 85.05 | 3,824.22 |
| Revenue | Two year | No | 56.6 | 60.01 | 3,396.88 |
| Revenue | One year | No | 41.7 | 62.51 | 2,604.97 |
| Revenue | Month-to-month | No | 21.0 | 61.46 | 1,292.76 |
| Revenue | Month-to-month | Yes | 14.0 | 73.02 | 1,023.51 |

**Row formatting:**
- Churned rows (Yes): Light Red `#FADBD8`
- Retained rows (No): Light Navy `#DAE3F3`

---

## Data Lineage & Referencing

**Fixed columns (typed manually):**
- Pillar, Segment Type, Contract, Churn Status — analytical additions not in source tables

**Referenced columns (cell references):**
- All numeric values — direct cell references from source sheets
- Example: `=revenue_by_contract!C2` for Two year Total Revenue

**Calculated columns (Excel formula):**
- Annualised Revenue at Risk — `=revenue_at_risk!A2*12`

**Naming conflict resolution:**
- Source table: `tbl_RevenueByContract` (on revenue_by_contract sheet)
- Analysis table: `tbl_RevenueByContractAnalysis` (on Revenue_Stability sheet)
- Convention: analysis tables use `Analysis` suffix to distinguish from source tables

---

## Charts Built

Three supporting charts built below the tables, arranged side by side.

### Chart 1 — Monthly Revenue at Risk vs Retained (Donut Chart)
- **Type:** Doughnut chart
- **Data:** Monthly Revenue Lost (£) and Monthly Revenue Retained (£) from Section 1
- **Colors:** Lost → Red `#C00000` / Retained → Dark Navy `#1F3864`
- **Data labels:** Percentage only — 31% and 69%
- **Label position:** Outside End
- **Donut hole size:** 60–65%
- **Legend:** Deleted — replaced with text box showing ■ Churned / ■ Retained with matching colors
- **Title:** `Monthly Revenue at Risk vs Retained`

### Chart 2 — Avg Revenue per Customer by Contract (Horizontal Bar)
- **Type:** Horizontal bar chart
- **Data:** Contract (C) and Avg Revenue per Customer (£) (E) from Section 2
- **Colors:** Two year → Gold `#C9A84C` / Others → Light Grey `#D9D9D9`
- **Data labels:** Yes — comma separator, no decimals
- **Gridlines:** Removed
- **X-axis:** Removed
- **Title:** `Avg Revenue per Customer by Contract Type`

### Chart 3 — Estimated LTV: Churned vs Retained (Horizontal Bar)
- **Type:** Horizontal bar chart — 6 individual bars ranked by LTV ascending
- **Data:** Contract (B) and Estimated LTV (F) from Section 4
- **Sort order:** Lowest LTV at top → highest LTV at bottom
- **Colors:** Churned rows → Red `#C00000` / Retained rows → Dark Navy `#1F3864`
- **Data labels:** Yes — comma separator
- **Legend:** Deleted — replaced with text box showing ■ Churned (Red) / ■ Retained (Dark Navy) with exact bar colors matched
- **Gridlines:** Removed
- **Title:** `Estimated LTV — Churned vs Retained by Contract`

---

## Key Revenue Findings Visualised

| Finding | Chart | Key Number |
|---|---|---|
| 30.5% of monthly revenue already lost | Chart 1 | £139,130.85 lost / £316,985.75 retained |
| Two-year customers generate 2.7x more revenue per customer | Chart 2 | £3,728.93 vs £1,369.25 |
| Two-year churned LTV is 5.2x higher than month-to-month churned | Chart 3 | £5,316.90 vs £1,023.51 |

---

## Design Decisions

**Why a donut chart for revenue at risk:**
The 31/69 split is a proportion story — part of a whole. Donut charts communicate proportions instantly. A bar chart would work but requires more cognitive effort to read the split. The donut makes the 30.5% loss visceral.

**Why percentage only on donut labels:**
The exact monetary values are already documented in the Revenue at Risk Summary block above the chart. The chart's job is to show the proportion visually — adding £ values to the donut segments creates label clutter without adding new information.

**Why individual bars not clustered for LTV chart:**
The key insight is the full ranking — two-year churned LTV at £5,316.90 vs month-to-month churned at £1,023.51. A ranked individual bar chart shows this ordering immediately. A clustered chart would group by contract type making the ranking comparison harder to read.

**Why text box legend instead of Excel auto-legend:**
Excel auto-generated a 6-entry legend for the LTV chart — one entry per bar — which was cluttered and misleading. A manual text box with just two entries (Churned / Retained) using exact bar colors is cleaner and more accurate.

---

## Validation Summary

| Check | Result |
|---|---|
| Section 1 summary block complete | ✅ |
| tbl_RevenueByContractAnalysis built and named | ✅ |
| tbl_RevenueByTierAnalysis built and named | ✅ |
| tbl_EstimatedLTVAnalysis built and named | ✅ |
| All values referenced from source sheets | ✅ |
| Annualised revenue at risk calculated correctly | ✅ |
| Row formatting applied per section | ✅ |
| Naming conflict resolved with Analysis suffix | ✅ |
| 3 charts built and formatted | ✅ |
| Data labels added to all charts | ✅ |
| Legends corrected with text box approach | ✅ |
| Sheet ready to feed dashboard | ✅ |

---

**Status:** Phase 5 complete — Revenue pillar analytical layer built and validated.  
*Project 7: Telco Customer Churn Analysis — Framework: Customer · Revenue · Risk*
