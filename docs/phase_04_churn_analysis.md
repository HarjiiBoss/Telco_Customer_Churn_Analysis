# Phase 4 — Churn & Retention Analysis

**Tool:** Microsoft Excel (Mac)
**Sheet:** `Churn_Analysis`
**Table:** `tbl_ChurnAnalysis`
**Charts Built:** 4
**Status:** Complete ✅

---

## Objective

Build a structured analytical layer combining churn data across all four Customer pillar dimensions into a single referenced table. Add calculated Annualised Revenue Loss and risk classification per segment. Build four supporting charts as the detailed evidence behind the Customer pillar KPIs.

---

## Sheet Structure

### Table — tbl_ChurnAnalysis

**Columns:**

| Column | Content | Source |
|---|---|---|
| Pillar | Customer — all rows | Typed manually |
| Segment Type | Contract / Tenure Band / Internet Service / Payment Method | Typed manually |
| Segment | Segment name | Typed manually |
| Total Customers | Customer count per segment | Cell reference from source sheet |
| Churned | Churned customer count | Cell reference from source sheet |
| Churn Rate (%) | Churn rate per segment | Cell reference from source sheet |
| Annualised Revenue Loss (£) | Churned × Avg Monthly Charge × 12 | Calculated in Excel |
| Risk Flag | 🔴 🟡 🟢 based on churn rate | Typed manually |

**Total rows:** 13 data rows across 4 dimensions

---

### Data Sources per Section

| Section | Rows | Source Sheet | Source Table |
|---|---|---|---|
| Contract | 2–4 | `churn_by_contract` | `tbl_ChurnByContract` |
| Tenure Band | 5–7 | `churn_by_tenure_band` | `tbl_ChurnByTenureBand` |
| Internet Service | 8–10 | `churn_by_internet_service` | `tbl_ChurnByInternetService` |
| Payment Method | 11–14 | `churn_by_payment_method` | `tbl_ChurnByPaymentMethod` |

---

## Full Table Output

| Pillar | Segment Type | Segment | Total Customers | Churned | Churn Rate (%) | Annualised Revenue Loss (£) | Risk Flag |
|---|---|---|---|---|---|---|---|
| Customer | Contract | Month-to-month | 3,875 | 1,655 | 42.71 | 1,478,378.40 | 🔴 High Risk |
| Customer | Contract | One year | 1,473 | 166 | 11.27 | 148,284.48 | 🟢 Stable |
| Customer | Contract | Two year | 1,695 | 48 | 2.83 | 42,877.44 | 🟢 Stable |
| Customer | Tenure Band | 0-12 months | 2,186 | 1,037 | 47.44 | 926,331.36 | 🔴 High Risk |
| Customer | Tenure Band | 13-36 months | 1,856 | 474 | 25.54 | 423,414.72 | 🟡 Moderate Risk |
| Customer | Tenure Band | 37+ months | 3,001 | 358 | 11.93 | 319,794.24 | 🟢 Stable |
| Customer | Internet Service | Fiber optic | 3,096 | 1,297 | 41.89 | 1,158,584.16 | 🔴 High Risk |
| Customer | Internet Service | DSL | 2,421 | 459 | 18.96 | 410,015.52 | 🟢 Stable |
| Customer | Internet Service | No internet | 1,526 | 113 | 7.40 | 100,940.64 | 🟢 Stable |
| Customer | Payment Method | Electronic check | 2,365 | 1,071 | 45.29 | 956,702.88 | 🔴 High Risk |
| Customer | Payment Method | Mailed check | 1,612 | 308 | 19.11 | 275,130.24 | 🟡 Moderate Risk |
| Customer | Payment Method | Bank transfer (automatic) | 1,544 | 258 | 16.71 | 230,466.24 | 🟢 Stable |
| Customer | Payment Method | Credit card (automatic) | 1,522 | 232 | 15.24 | 207,240.96 | 🟢 Stable |

---

## Annualised Revenue Loss Calculation

**Formula:**
```
= Churned × Avg Monthly Charge (churned) × 12
```

**Avg Monthly Charge (churned):** £74.44 — sourced from `tbl_AvgChargesByChurn`, locked as `$C$3` to prevent shifting when formula is copied down.

**Example — Month-to-month:**
```
1,655 × 74.44 × 12 = £1,478,378.40
```

**Rationale:** Annualised figure is more meaningful to business stakeholders than monthly — decisions around retention investment, campaign budgets and lifetime value are made on an annual basis.

---

## Risk Flag Logic

| Churn Rate | Risk Flag |
|---|---|
| ≥ 40% | 🔴 High Risk |
| 20–39% | 🟡 Moderate Risk |
| < 20% | 🟢 Stable |

---

## Row Formatting

| Risk Level | Background | Text |
|---|---|---|
| 🔴 High Risk | Light Red `#FADBD8` | Dark Grey `#262626` |
| 🟡 Moderate Risk | Light Gold `#FDF2D0` | Dark Grey `#262626` |
| 🟢 Stable | White `#FFFFFF` | Dark Grey `#262626` |

---

## Referencing Approach

**Fixed columns (typed manually):**
- Pillar, Segment Type, Segment, Risk Flag — analytical additions not present in source tables

**Referenced columns (cell references):**
- Total Customers, Churned, Churn Rate (%) — direct cell references from source sheets
- Example: `=churn_by_contract!B2` for Month-to-month Total Customers

**Calculated columns (Excel formula):**
- Annualised Revenue Loss — `=E2*avg_charges_by_churn!$C$3*12`

**Workflow principle applied:**
- SQL = computation layer — all aggregation done in Phase 1
- Excel = presentation layer — references and organises SQL outputs
- No recalculation of SQL-computed metrics in Excel

---

## Charts Built

Four supporting charts built below the table starting at row 17, arranged in a 2×2 grid.

### Chart 1 — Churn Rate by Contract Type
- **Type:** Horizontal bar chart
- **Data:** Segment (C2:C4) and Churn Rate (%) (F2:F4)
- **Colors:** Month-to-month → Gold `#C9A84C` / Others → Light Grey `#D9D9D9`
- **Data labels:** Yes — 1 decimal place, no % symbol
- **Gridlines:** Removed
- **X-axis:** Removed

### Chart 2 — Churn Rate by Tenure Band
- **Type:** Horizontal bar chart
- **Data:** Segment (C5:C7) and Churn Rate (%) (F5:F7)
- **Colors:** 0-12 months → Red `#C00000` / Others → Light Grey `#D9D9D9`
- **Data labels:** Yes — 1 decimal place, no % symbol
- **Gridlines:** Removed
- **X-axis:** Removed

### Chart 3 — Churn Rate by Internet Service
- **Type:** Horizontal bar chart
- **Data:** Segment (C8:C10) and Churn Rate (%) (F8:F10)
- **Colors:** Fiber optic → Gold `#C9A84C` / Others → Light Grey `#D9D9D9`
- **Data labels:** Yes — 1 decimal place, no % symbol
- **Gridlines:** Removed
- **X-axis:** Removed

### Chart 4 — Churn Rate by Payment Method
- **Type:** Horizontal bar chart
- **Data:** Segment (C11:C14) and Churn Rate (%) (F11:F14)
- **Colors:** Electronic check → Red `#C00000` / Others → Light Grey `#D9D9D9`
- **Data labels:** Yes — 1 decimal place, no % symbol
- **Gridlines:** Removed
- **X-axis:** Removed

---

## Design Decisions

**Why horizontal bar charts:**
Horizontal bars are the clearest format for comparing categories with text labels. Vertical bars work better for time series — horizontal bars work better for ranked categorical comparisons like churn rate by segment.

**Why no % symbol on data labels:**
The chart title already communicates that values are churn rates. Adding % to each label adds visual noise without adding information. Clean numbers read faster.

**Why no x-axis:**
Once data labels are added the x-axis scale becomes redundant. Removing it reduces clutter and draws the eye directly to the bars and labels.

**Why Gold for primary risk bar, Red for highest risk:**
Gold signals the primary finding — the segment that drives the story in each chart. Red signals the most urgent risk. This distinction carries the same meaning across all four charts consistently.

---

## Validation Summary

| Check | Result |
|---|---|
| All 13 rows populated | ✅ |
| All references verified against source tables | ✅ |
| Annualised Revenue Loss formula correct | ✅ |
| Risk flags consistent with churn rate logic | ✅ |
| Table converted to tbl_ChurnAnalysis | ✅ |
| Row formatting applied | ✅ |
| 4 charts built and formatted | ✅ |
| Data labels added, gridlines and x-axis removed | ✅ |
| Sheet ready to feed dashboard | ✅ |

---

**Status:** Phase 4 complete — Customer pillar analytical layer built and validated.  
*Project 7: Telco Customer Churn Analysis — Framework: Customer · Revenue · Risk*
