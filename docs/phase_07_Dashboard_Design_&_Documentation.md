# Phase 7 — Dashboard Design & Documentation

**Tool:** Microsoft Excel (Mac)  
**Workbook:** `Telco_Churn_Analysis.xlsx`  
**Dashboards:** 4 (Executive Summary · Customer Analysis · Revenue Stability · Segment Risk)  
**Status:** Complete ✅

---

## Objective

Design a consistent executive reporting interface that communicates customer churn, financial impact, and structural business risk through four interconnected dashboards. Apply a standardized visual design system to ensure clarity, consistency, and ease of interpretation across all dashboard pages.

The dashboards are built on the KPI framework and analytical layers developed in Phases 3–6, ensuring every visual traces directly back to validated SQL outputs.

---

# Dashboard Architecture

The reporting workflow follows a layered storytelling approach.

```text
Executive Summary
        ↓
Customer Analysis
        ↓
Revenue Stability
        ↓
Segment Risk
```

The Executive Summary presents the overall business situation, while the three supporting dashboards provide progressively deeper analysis across the Customer, Revenue, and Risk pillars.

---

## Dashboard Purpose

| Dashboard | Purpose | Primary Audience |
|---|---|---|
| Executive Summary | Present headline KPIs, financial impact, and priority business risks | Executive Leadership |
| Customer Analysis | Explain who is churning and identify the strongest behavioural drivers | Customer Success · Marketing |
| Revenue Stability | Quantify financial exposure and customer value | Finance · Commercial |
| Segment Risk | Identify structural concentration risk and vulnerable customer segments | Executive Leadership · Strategy |

---

# Dashboard Design System

A consistent visual design system was applied across all dashboard pages to improve readability, reduce cognitive load, and create a unified reporting experience.

---

## Colour Palette

| Purpose | Colour | Hex Code |
|---|---|---|
| Primary Brand | Dark Navy | `#1F3864` |
| KPI Highlight | Gold | `#C9A84C` |
| Critical Risk | Red | `#C00000` |
| Secondary Background | Light Navy | `#DAE3F3` |
| Moderate Risk | Light Gold | `#FDF2D0` |
| High Risk Row | Light Red | `#FADBD8` |
| Secondary Elements | Light Grey | `#D9D9D9` |
| Primary Text | Dark Grey | `#262626` |
| Secondary Text | Muted Blue-Grey | `#A9B4C2` |
| Background | White | `#FFFFFF` |

---

## Typography

| Element | Font Size | Weight |
|---|---:|---|
| Dashboard Title | 14 pt | Bold |
| Dashboard Subtitle | 9 pt | Regular |
| KPI Value | 36 pt | Bold |
| KPI Label | 11 pt | Bold |
| Chart Title | 10 pt | Bold |
| Chart Axis Labels | 8 pt | Regular |
| Chart Data Labels | 9 pt | Regular |
| Insight Box Title | 11 pt | Bold |
| Insight Box Text | 9 pt | Regular |
| Footer | 8 pt | Regular |

---

## Layout Standards

| Component | Standard |
|---|---|
| Sheet background | White |
| Chart background | No fill |
| Dashboard title | Left aligned |
| Subtitle | Left aligned |
| Visual hierarchy | KPI Cards → Charts → Business Insights → Recommendations |
| KPI internal padding | 8–10 pt |
| KPI corner radius | 6 pt |
| Footer alignment | Right aligned |
| Dashboard spacing | Consistent alignment and margins across all pages |

---

## KPI Card Standards

| Element | Standard |
|---|---|
| Background | Dark Navy |
| KPI Value | Gold |
| KPI Label | Muted Blue-Grey |
| Shape | Rounded rectangle |
| Border | None |
| Purpose | Highlight headline business metrics consistently across dashboards |

---

## Chart Standards

| Element | Standard |
|---|---|
| Background | No fill |
| Border | None |
| Gridlines | Removed |
| Primary highlight | Gold |
| Highest-risk category | Red |
| Secondary categories | Light Grey |
| Stable category | Dark Navy |
| Data labels | Enabled |
| Legends | Removed where redundant |
| Axes | Removed when unnecessary |
| Chart titles | Dark Navy, Bold |

---

## Insight Panel Standards

Each dashboard contains a dedicated insight panel summarising the most important business findings.

| Element | Standard |
|---|---|
| Background | Dark Navy |
| Heading | Gold |
| Body text | Muted Blue-Grey |
| Content | Three concise evidence-based business insights |

---

## Recommendation Panel Standards

Each supporting dashboard concludes with actionable recommendations linked directly to the analytical findings.

| Element | Standard |
|---|---|
| Background | White |
| Border | Light Grey |
| Heading | Dark Navy |
| Body text | Dark Grey |
| Content | Practical business actions supported by dashboard evidence |

---

# Dashboard Documentation

---

# Dashboard 1 — Executive Summary

## Objective

Provide a high-level overview of customer churn, revenue exposure, and structural business risk through headline KPIs, supporting visualisations, executive insights, and strategic recommendations.

---

## Dashboard Components

### KPI Cards

- Overall Churn Rate
- Monthly Revenue at Risk
- Revenue at Risk (%)
- High-Risk Customer Count

### Supporting Visuals

- Monthly Revenue at Risk vs Retained (Donut Chart)

### Executive Insight Panel

Highlights the three most significant findings impacting business performance.

### Executive Recommendation Panel

Summarises the highest-priority retention initiatives based on the supporting analysis.

---

## Executive Story

The dashboard establishes the overall business situation by showing that customer churn is creating significant financial exposure, driven primarily by month-to-month customers, early-tenure customers, and identifiable high-risk customer segments.

---

# Dashboard 2 — Customer Analysis

## Objective

Identify the customer segments most likely to churn and explain the behavioural factors driving customer attrition.

---

## Dashboard Components

### KPI Cards

- Overall Churn Rate
- Month-to-Month Churn Rate
- Early Tenure Churn Rate
- Average Tenure (Churned)

### Supporting Charts

- Churn Rate by Contract Type
- Churn Rate by Tenure Band
- Churn Rate by Internet Service
- Churn Rate by Payment Method

### Customer Insights

Summarises the strongest behavioural churn drivers identified during SQL analysis.

### Recommended Actions

Provides targeted retention initiatives focused on contract migration, onboarding, and payment behaviour.

---

## Business Story

Customer churn is concentrated within identifiable behavioural segments. Month-to-month contracts, early-tenure customers, and electronic check payment users represent the strongest predictors of customer attrition.

---

# Dashboard 3 — Revenue Stability

## Objective

Measure the financial impact of customer churn by analysing revenue exposure, customer value, and estimated lifetime value across contract types.

---

## Dashboard Components

### KPI Cards

- Monthly Revenue at Risk
- Revenue at Risk (%)
- Average Monthly Charge (Churned)

### Supporting Charts

- Monthly Revenue at Risk vs Retained
- Average Revenue per Customer by Contract Type
- Estimated LTV — Churned vs Retained by Contract

### Revenue Insights

Summarises the financial implications of customer churn.

### Recommended Actions

Focuses on retaining high-value customers and increasing long-term contract adoption.

---

## Business Story

Customer churn disproportionately affects higher-value customers, creating significant revenue exposure. Long-term contracts substantially increase customer value, making retention of premium customers a strategic priority.

---

# Dashboard 4 — Segment Risk

## Objective

Identify structural business risks by analysing customer concentration, revenue concentration, and high-risk customer profiles.

---

## Dashboard Components

### KPI Cards

- Month-to-Month Revenue Share
- Fiber Revenue Share
- High-Risk Customer Count

### Supporting Charts

- Contract Type — Customer & Revenue Concentration
- Internet Service — Revenue Concentration vs Churn Rate
- High Risk vs Standard Customers — Churn Rate Comparison

### Risk Insights

Summarises the structural vulnerabilities identified across contract and service segments.

### Recommended Actions

Recommends reducing dependency on high-risk segments through targeted retention and diversification strategies.

---

## Business Story

The business is structurally exposed to customer churn due to revenue concentration within month-to-month contracts, fiber optic services, and a clearly identifiable high-risk customer segment.

---

# Dashboard Design Principles

The dashboards were developed using a consistent set of reporting principles.

### SQL as the Computation Layer

All business metrics are calculated in MySQL. Excel references validated SQL outputs without duplicating analytical logic.

### Single Source of Truth

Every KPI displayed on the dashboards can be traced directly back to SQL outputs through the structured analysis sheets developed in earlier phases.

### Layered Reporting

Customer, Revenue, and Risk analytical layers separate business analysis from presentation, improving maintainability and reducing duplication.

### Executive-First Storytelling

Each dashboard answers a specific business question before progressing to supporting evidence and actionable recommendations.

### Consistent Visual Language

Colours, typography, spacing, and chart formatting remain consistent across all dashboards to improve readability and create a unified reporting experience.

### Minimalist Dashboard Design

Unnecessary gridlines, borders, legends, and chart elements were removed to maximise focus on business insights rather than visual decoration.

---

# Validation Summary

| Check | Result |
|---|---|
| Four dashboards completed | ✅ |
| Common design system applied | ✅ |
| Colour palette standardised | ✅ |
| Typography standardised | ✅ |
| KPI cards consistent across dashboards | ✅ |
| Chart formatting standardised | ✅ |
| Business insight panels included | ✅ |
| Recommendation panels included | ✅ |
| Dashboard navigation follows analytical framework | ✅ |
| All dashboard metrics traceable to SQL outputs | ✅ |
| Ready for executive presentation | ✅ |

---

# Outcome

A four-dashboard executive reporting solution was successfully developed, translating validated SQL analysis into clear, actionable business intelligence. By combining consistent visual design with structured storytelling, the dashboards enable stakeholders to understand customer behaviour, quantify financial impact, identify structural risks, and prioritise data-driven retention strategies.

---

**Status:** Phase 7 complete — executive dashboards designed, documented, validated, and ready for presentation.
*Project 7: Telco Customer Churn Analysis — Framework: Customer · Revenue · Risk*
