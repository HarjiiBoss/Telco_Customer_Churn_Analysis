# Phase 6 — Segment & Concentration Risk Analysis

**Tool:** Microsoft Excel (Mac)  
**Sheet:** `Segment_Risk`  
**Tables:** `tbl_ContractConcentrationRisk` · `tbl_InternetServiceRisk` · `tbl_HighRiskProfile`  
**Charts Built:** 3  
**Status:** Complete ✅

---

## Objective

Build the Risk pillar analytical layer combining contract concentration, internet service concentration and high-risk customer profile data into a structured, presentation-ready sheet. This sheet feeds `Dashboard_Risk` and contributes the structural risk story to the Executive Summary Dashboard.

---

## Sheet Structure

### Section 1 — Contract Concentration Risk

**Table:** `tbl_ContractConcentrationRisk`
**Source:** `tbl_ConcentrationRisk` (concentration_risk sheet)

| Pillar | Segment Type | Segment | Total Customers | Customer Share (%) | Monthly Revenue (£) | Revenue Share (%) |
|---|---|---|---|---|---|---|
| Risk | Contract | Month-to-month | 3,875 | 55.02 | 257,294.15 | 56.41 |
| Risk | Contract | Two year | 1,695 | 24.07 | 103,005.85 | 22.58 |
| Risk | Contract | One year | 1,473 | 20.91 | 95,816.60 | 21.01 |

**Row formatting:**

| Segment | Background | Text |
|---|---|---|
| Month-to-month | Light Red `#FADBD8` | Dark Grey `#262626` |
| Two year | Light Navy `#DAE3F3` | Dark Grey `#262626` |
| One year | White `#FFFFFF` | Dark Grey `#262626` |

**Key finding:** Month-to-month holds 55.02% of customers and 56.41% of monthly revenue — the majority of the business sits on the most fragile contract type.

---

### Section 2 — Internet Service Concentration Risk

**Table:** `tbl_InternetServiceRisk`
**Source:** `tbl_InternetServiceConcentration` (internet_service_concentration sheet)

| Pillar | Segment Type | Segment | Total Customers | Customer Share (%) | Monthly Revenue (£) | Revenue Share (%) | Churn Rate (%) |
|---|---|---|---|---|---|---|---|
| Risk | Internet Service | Fiber optic | 3,096 | 43.96 | 283,284.40 | 62.11 | 41.89 |
| Risk | Internet Service | DSL | 2,421 | 34.37 | 140,665.35 | 30.84 | 18.96 |
| Risk | Internet Service | No internet | 1,526 | 21.67 | 32,166.85 | 7.05 | 7.40 |

**Row formatting:**

| Segment | Background | Text |
|---|---|---|
| Fiber optic | Light Red `#FADBD8` | Dark Grey `#262626` |
| DSL | Light Gold `#FDF2D0` | Dark Grey `#262626` |
| No internet | Light Navy `#DAE3F3` | Dark Grey `#262626` |

**Key finding:** Fiber optic generates 62.11% of monthly revenue yet churns at 41.89% — the highest revenue concentration in the most volatile service type.

---

### Section 3 — High-Risk Customer Profile

**Table:** `tbl_HighRiskProfile`
**Source:** `tbl_HighRiskCustomers` (high_risk_customers sheet)

**High-risk definition:** Month-to-month contract + MonthlyCharges > £70 + tenure < 12 months

| Pillar | Risk Segment | Total Customers | Churned | Churn Rate (%) |
|---|---|---|---|---|
| Risk | High Risk | 814 | 566 | 69.53 |
| Risk | Standard | 6,229 | 1,303 | 20.92 |

**Row formatting:**

| Segment | Background | Text |
|---|---|---|
| High Risk | Light Red `#FADBD8` | Dark Grey `#262626` |
| Standard | Light Navy `#DAE3F3` | Dark Grey `#262626` |

**Key finding:** High-risk customers churn at 69.53% — 3.3x the standard rate of 20.92%. 814 identifiable customers carry all three high-risk signals simultaneously.

---

## Referencing Approach

**Fixed columns (typed manually):**
- Pillar, Segment Type, Segment, Risk Segment — analytical additions not in source tables

**Referenced columns (cell references):**
- All numeric values — direct cell references from source sheets
- Example: `=concentration_risk!B2` for Month-to-month Total Customers

**No calculated columns:**
- All values come directly from SQL outputs — no additional Excel calculations required in this phase

**Naming convention:**
- Source tables: `tbl_ConcentrationRisk`, `tbl_InternetServiceConcentration`, `tbl_HighRiskCustomers`
- Analysis tables: `tbl_ContractConcentrationRisk`, `tbl_InternetServiceRisk`, `tbl_HighRiskProfile`
- Analysis suffix applied consistently to avoid naming conflicts

---

## Charts Built

Three supporting charts built below the tables starting at row 17, arranged side by side.

### Chart 1 — Contract Type: Customer & Revenue Concentration (Clustered Bar)
- **Type:** Clustered horizontal bar chart
- **Data:** Segment (C2:C4), Customer Share % (E2:E4), Revenue Share % (G2:G4)
- **Colors:** Customer Share → Dark Navy `#1F3864` / Revenue Share → Gold `#C9A84C`
- **Data labels:** Yes — 1 decimal place, no % symbol
- **Gridlines:** Removed
- **X-axis:** Removed
- **Legend:** Customer Share / Revenue Share
- **Title:** `Contract Type — Customer & Revenue Concentration`
- **Story:** Month-to-month dominates both customer share and revenue share — structural fragility confirmed

### Chart 2 — Internet Service: Revenue Concentration vs Churn Rate (Clustered Bar)
- **Type:** Clustered horizontal bar chart
- **Data:** Segment (C7:C9), Revenue Share % (G7:G9), Churn Rate % (H7:H9)
- **Colors:** Revenue Share → Dark Navy `#1F3864` / Churn Rate → Red `#C00000`
- **Data labels:** Yes — 1 decimal place
- **Gridlines:** Removed
- **X-axis:** Removed
- **Legend:** Revenue Share / Churn Rate
- **Title:** `Internet Service — Revenue Concentration vs Churn Rate`
- **Story:** Fiber optic carries 62.11% revenue share alongside 41.89% churn — compounded risk in a single service type

### Chart 3 — High Risk vs Standard: Churn Rate Comparison (Horizontal Bar)
- **Type:** Horizontal bar chart — 2 bars
- **Data:** Risk Segment (B12:B13) and Churn Rate % (E12:E13)
- **Colors:** High Risk → Red `#C00000` / Standard → Dark Navy `#1F3864`
- **Data labels:** Yes — 1 decimal place
- **Gridlines:** Removed
- **X-axis:** Removed
- **Legend:** Not needed — bar labels are self-explanatory
- **Title:** `High Risk vs Standard Customers — Churn Rate`
- **Story:** 69.53% vs 20.92% — high-risk customers churn at 3.3x the standard rate

---

## Key Risk Findings Visualised

| Finding | Chart | Key Number |
|---|---|---|
| Month-to-month dominates customer and revenue base | Chart 1 | 55.02% customers / 56.41% revenue |
| Fiber optic: highest revenue, highest churn | Chart 2 | 62.11% revenue share / 41.89% churn rate |
| High-risk customers identified and quantified | Chart 3 | 69.53% vs 20.92% churn rate |

---

## Design Decisions

**Why clustered bar for Charts 1 and 2:**
Both charts compare two metrics side by side per segment — customer share vs revenue share, and revenue share vs churn rate. Clustered bars are the clearest format for this type of dual-metric comparison. The side-by-side layout makes it immediately obvious when two metrics are aligned (Month-to-month: both share metrics high) or divergent (Fiber optic: high revenue share but also high churn).

**Why simple horizontal bar for Chart 3:**
Only one metric being compared across two segments — churn rate. A simple two-bar horizontal chart is cleaner and more impactful than a clustered chart for a binary comparison. The stark difference between 69.53% and 20.92% speaks for itself without needing additional complexity.

**Why no legend on Chart 3:**
The bar labels (High Risk / Standard) already identify each segment. Adding a legend would be redundant and would clutter a chart that works precisely because of its simplicity.

**Why Fiber optic row uses Light Gold not Light Red in Section 2:**
Fiber optic is the highest revenue concentration risk but it's not a binary high/low situation — it sits alongside DSL and No internet in a gradient. Light Gold signals elevated concern without overwhelming the table with red. The chart communicates the severity more effectively than row color alone.

---

## Validation Summary

| Check | Result |
|---|---|
| tbl_ContractConcentrationRisk built and named | ✅ |
| tbl_InternetServiceRisk built and named | ✅ |
| tbl_HighRiskProfile built and named | ✅ |
| All values referenced from source sheets | ✅ |
| No recalculation of SQL-computed metrics | ✅ |
| Row formatting applied per section | ✅ |
| Naming conflicts resolved with Analysis suffix | ✅ |
| 3 charts built and formatted | ✅ |
| Data labels added to all charts | ✅ |
| Gridlines and x-axis removed from all charts | ✅ |
| Sheet ready to feed dashboard | ✅ |

---

**Status:** Phase 6 complete — Risk pillar analytical layer built and validated.  
*Project 7: Telco Customer Churn Analysis — Framework: Customer · Revenue · Risk*
