# Documentation Index

Central list of the project's documents. The project was run in eleven phases before the Data Analysis Playbook settled on six; the phase records are kept as written at the time, and the table below maps them to the playbook phases.

---

# Documents

| Document | Purpose | Status | Last Updated |
|----------|---------|--------|--------------|
| [README.md](../README.md) | Results, approach, reproducibility, corrections and published surfaces | ☑ Complete | 2026-10-29 |
| [PROJECT_INFO.md](../PROJECT_INFO.md) | Project charter, written retrospectively: question, scope, metric definitions, risks, assumptions | ☑ Complete | 2026-10-29 |
| [executive_summary.md](executive_summary.md) | Findings, recommendations and limitations for decision-makers | ☑ Complete | 2026-10-29 |
| [data_dictionary.md](data_dictionary.md) | Every table and column in the workbook | ☑ Complete (moved from the repository root on 2026-10-29) | 2026-10-29 |
| [index.html](index.html) | Project page, published at taofeeksalami.com/Telco_Customer_Churn_Analysis | ☑ Complete | 2026-10-29 |
| [../.figures-allow](../.figures-allow) | Derived figures checked by hand, with their calculations | ☑ Complete | 2026-10-29 |

---

# Phase Records

| Phase | Document | Playbook phase | Notes |
|-------|----------|----------------|-------|
| 0 | [phase_00_setup.md](phase_00_setup.md) | 0 Scoping & setup; 1 Data preparation | Schema, import, row count, `TotalCharges` cleaning |
| 1 | [phase_01_sql.md](phase_01_sql.md) | 1 Exploration; 2 Business analysis | 22 queries and their results. Carries a correction note |
| 2 | [phase_02_excel_data_model.md](phase_02_excel_data_model.md) | 2 Business analysis | Power Query import and validation of the 17 CSV files |
| 3 | [phase_03_kpi_framework.md](phase_03_kpi_framework.md) | 2 Business analysis | The 10-KPI framework. Carries a correction note |
| 4 | [phase_04_churn_analysis.md](phase_04_churn_analysis.md) | 2 Business analysis | Customer pillar sheet and charts |
| 5 | [phase_05_revenue_stability.md](phase_05_revenue_stability.md) | 2 Business analysis | Revenue pillar sheet and charts. Carries a correction note |
| 6 | [phase_06_segment_risk.md](phase_06_segment_risk.md) | 2 Business analysis | Risk pillar sheet and charts. Carries a correction note |
| 7 | [phase_07_dashboard_design_and_documentation.md](phase_07_dashboard_design_and_documentation.md) | 5 Reporting | Dashboard design. Carries a correction note |
| 8 | [phase_08_business_insights_and_recommendations.md](phase_08_business_insights_and_recommendations.md) | 5 Reporting | Insights and recommendations. Carries a correction note; the executive summary is the current version |
| 9 | [phase_09_readme_and_documentation.md](phase_09_readme_and_documentation.md) | 5 Reporting | README and documentation as first written |
| 10 | [phase_10_project_polish_and_export.md](phase_10_project_polish_and_export.md) | 5 Reporting | Final checks and export |

Playbook phases 3 (method selection) and 4 (advanced analytics) were not needed: every question was answered with descriptive SQL.

---

# Not Created

These documents are part of the playbook's standard set but were not kept during the project. They are not reconstructed after the fact, because they would add records nobody kept at the time.

| Document | Where the content is instead |
|----------|------------------------------|
| Cleaning log | The only cleaning step (11 blank `TotalCharges` set to NULL) is recorded in phase_00_setup.md |
| Assumption register | The main assumptions are listed in PROJECT_INFO.md → Assumptions |
| Project glossary | Terms are defined in PROJECT_INFO.md → Metric Definitions |
| Security notes | The project uses a local MySQL instance and no credentials; nothing sensitive is stored in the repository |
