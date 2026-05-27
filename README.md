# Olist E-Commerce Business Analysis (2016–2018)

[![Analysis Period](https://img.shields.io/badge/Analysis_Period-2016--2018-blue)](https://github.com/varneet-s/olist-analysis/blob/main)
[![Dataset Size](https://img.shields.io/badge/Orders_Analyzed-96%2C478-green)](https://github.com/varneet-s/olist-analysis/blob/main)
[![Tools](https://img.shields.io/badge/Tools-Excel%20%7C%20Tableau%20%7C%20draw.io-orange)](https://github.com/varneet-s/olist-analysis/blob/main)
[![Status](https://img.shields.io/badge/Status-Complete-success)](https://github.com/varneet-s/olist-analysis/blob/main)
[![Documentation](https://img.shields.io/badge/Docs-9_Markdown_Files-informational)](https://github.com/varneet-s/olist-analysis/blob/main)

## Table of Contents

1. [Executive Summary](#executive-summary)
2. [Quick Start](#quick-start)
3. [Dashboard Preview](#dashboard-preview)
4. [Business Problem](#business-problem)
5. [Project Structure](#project-structure)
6. [Key Findings](#key-findings)
7. [Next Steps](#next-steps)
8. [What This Analysis Demonstrates](#what-this-analysis-demonstrates)
9. [Dataset & Repository](#dataset--repository)

---

## Executive Summary

What happens when 42% of an e-commerce platform's revenue depends on a single state, and customers in other regions pay more for shipping than for products? This analysis traces three years of Olist's Brazilian marketplace data to answer that question and quantify what it costs.

Olist, a Brazilian e-commerce marketplace aggregator, faced severe geographic concentration during 2016–2018. I analysed 96,478 delivered orders across Brazil's 27 states using Excel pivot tables and Tableau dashboards, testing four business questions across delivery performance, revenue concentration, seller distribution, and freight burden. The analysis traced all three business risks to a single structural root cause.

---

## Quick Start

**For recruiters/hiring managers:** Review the [Dashboard Preview](#dashboard-preview) and [Key Findings](#key-findings) (5 min read).

**For analysts/peers:** Start with [Analysis](4-analysis.md) for a complete walkthrough of how each metric was built (20 min read).

**For business stakeholders:** Jump to [Business Recommendations](7-business-recommendations.md) for prioritised, actionable interventions (10 min read).

**To explore the data:** Download `data/Olist_Business_Analysis.xlsx` or view `dashboard/Olist_Analysis_Dashboard.pptx`.

---

## Dashboard Preview

[![Olist E-Commerce Dashboard](images/dashboard_full_view.png)](images/dashboard_full_view.png)

The dashboard visualises delivery performance patterns, geographic revenue distribution, seller concentration, and freight cost variations across Brazil's 27 states. Tableau visualisations include:

- **Delay Severity vs. Review Score** — Progressive satisfaction degradation by delay band
- **Revenue by State** — Geographic distribution of platform GMV
- **GMV Pareto Curve** — Lorenz curve showing seller concentration patterns
- **Freight % by State** — Regional freight burden comparison
- **Monthly Growth Trend** — Platform order volume evolution over time
- **Geographic Maps** — Customer distribution vs. seller concentration

Full dashboard available in `dashboard/Olist_Analysis_Dashboard.pptx`.

---

## Business Problem

Olist faced three interconnected structural gaps that limited sustainable growth and created revenue vulnerability:

1. **Freight Cost Inequality**: Customers in remote regions paid disproportionately high freight costs compared to major urban centres, suppressing demand through a "distance tax."
2. **Delivery Performance Collapse**: Late deliveries caused significant review score degradation — creating customer retention challenges and damaging repeat purchase behaviour.
3. **Geographic Revenue Concentration**: Platform revenue was heavily concentrated in a small number of states, exposing the business to regional economic shocks and growth saturation.

These gaps were causally linked: seller concentration patterns forced most orders into long-haul fulfilment, which drove both high freight costs and increased late delivery risk in remote regions.

Four business questions guided the analysis — predictions, test methods, and validation results documented in [Business Problem Diagnosis](1-business-problem-diagnosis.md).

---

## Project Structure

This analysis follows the Business Analyst workflow from problem identification through actionable recommendations:

### 1. [Business Problem Diagnosis](1-business-problem-diagnosis.md)

Defines Olist's operating model and the structural geographic concentration problem. Uses the **6P framework** to form four business questions before opening the dataset — predictions and test methods documented here.

### 2. [Stakeholder Map](2-stakeholder-map.md)

Identifies all parties impacted by or influencing the analysis. Classifies them using a **Power/Interest Grid (RACI framework)** and determines engagement strategies for each group (CEO, Operations, Sales, Investors, Sellers, Customers).

### 3. [Current State (AS-IS)](3-current-state.md)

Maps the order fulfilment process using a **BPMN swimlane diagram** across four actors (Customer, Olist System, Seller, Carrier). Identifies three sequential handoff points where delays accumulate and explains why the current workflow fails for long-distance orders.

### 4. [Analysis](4-analysis.md)

Documents every step of the data analysis using the **STAR framework** (Situation, Task, Action, Result):

- **Phase 1:** Data ingestion & consolidation — 9 CSVs joined into MASTER sheet using XLOOKUPs
- **Phase 2:** Data cleaning & filtering — 96,478 delivered orders, 8 calculated columns
- **Phase 3:** Data Analysis — 6 pivot tables testing H1–H4
- **Phase 4:** Data Visualisation — 7 visualisations, including a GMV Pareto curve built with 8 custom Tableau calculated fields

Shows exact formulas, business logic behind each metric, and analytical decisions at each phase.

### 5. [Gap Analysis](5-gap-analysis.md)

Quantifies the distance between current performance (AS-IS) and desired future state (TO-BE) across three dimensions. Applies the **Nadler-Tushman Congruence Model** to diagnose root causes across Work, People, Structure, and Culture. Concludes that seller concentration drives all other gaps.

### 6. [Insights](6-insights.md)

Translates analytical findings into strategic business implications:
- Late delivery impact on customer lifetime value
- Geographic concentration risks
- Pareto concentration implications
- Distance tax effects on order volume
- Seller concentration as root cause
- Growth ceiling analysis

### 7. [Business Recommendations](7-business-recommendations.md)

Three prioritised, actionable recommendations with expected impact, owner, effort, and **MoSCoW prioritisation**:

1. **Logistics partnerships in northern states** — Reduce freight costs in remote regions
2. **Reduce transit time in remote routes** — Address late delivery rate and protect review scores
3. **Seller acquisition in underserved states** — Reduce revenue concentration and shorten fulfilment distances

### 8. [Data Dictionary](8-data-dictionary.md)

Technical reference documenting all 8 Excel calculated columns (`delivery_delay_days`, `delivery_status`, `delay_band`, `freight_pct`, etc.) and 8 Tableau calculated fields (`True GMV`, `Concentration Ratio`, `Top 20% Sellers GMV`, etc.) — with exact formulas, data types, and business logic for each metric.

---

## Key Findings

**1. Late deliveries collapse customer satisfaction**

- On-time deliveries averaged **4.03** review score; late deliveries averaged **2.27** — a 1.76-point gap on a 5-point scale
- Orders 7+ days late dropped to **1.70** — below the threshold where repeat purchase recovery becomes unlikely

**2. São Paulo controls 42% of platform revenue**

- Top 3 states (SP, RJ, MG) generated approximately **70% of GMV**
- Monthly orders peaked at **7,289** (Nov 2017), then plateaued at 6,000–7,000/month — indicating market saturation

**3. Top 20% of sellers generate 82.5% of GMV**

- 592 of 2,960 sellers drive the majority of platform revenue — stronger concentration than the classic 80/20 split
- Platform health depends on retaining a small, identifiable cohort

**4. Northern customers pay freight that can exceed product price**

- Roraima: ~60%, Rondônia: ~58%, Maranhão: ~54% of product price in freight costs
- São Paulo baseline: ~25% — customers in remote states pay more than double

**5. Seller concentration in SP is the root cause of all three gaps**

- Most sellers operate from SP → long-haul fulfilment to the rest of Brazil → higher freight costs and higher late delivery risk
- Solving distribution at the seller level would address all three business problems simultaneously

---

## Next Steps

### Short-Term
- Validate recommendations with Operations and Sales teams through stakeholder workshops
- Develop an implementation roadmap for carrier partnership negotiations
- Design a pilot programme for seller acquisition in 2–3 underserved states

### Medium-Term
- Monitor late delivery rate improvements post-carrier optimisation
- Track revenue diversification metrics across geographic regions
- Measure customer satisfaction changes in targeted intervention states

### Further Analysis
- **Customer lifetime value modelling:** Calculate actual CLV impact of late deliveries using repeat purchase data
- **Predictive delivery risk model:** Logistic regression predicting late delivery probability based on distance, infrastructure, and order characteristics
- **Category-level analysis:** Identify which product categories carry the highest freight sensitivity
- **Seasonality deep-dive:** Investigate whether peak periods create systematic delivery bottlenecks
- **Seller churn analysis:** Correlate high-GMV seller activity reduction with delivery performance by region

---

## What This Analysis Demonstrates

### Business Analysis Skills

- **Problem structuring:** Used the 6P framework to identify plausible problems before opening data
- **Business question formation:** Documented testable predictions to guide analysis and avoid retrofitting conclusions
- **Stakeholder management:** Mapped 6 stakeholder groups using Power/Interest Grid (RACI)
- **Process mapping:** Created BPMN swimlane diagram showing order fulfilment workflow
- **Root cause diagnosis:** Applied Nadler-Tushman Congruence Model across Work–People–Structure–Culture
- **Gap quantification:** Calculated AS-IS vs. TO-BE targets with specific improvement ranges
- **Recommendation prioritisation:** Used MoSCoW framework with effort/impact assessment

### Data Analysis Skills

- **Data engineering:** Consolidated 9 CSV files using XLOOKUP, handling many-to-many relationships correctly
- **Data transformation:** Built 8 calculated columns with documented business logic
- **Pivot table analysis:** Created 6 pivot tables, each testing a specific business question
- **Statistical analysis:** Calculated averages, concentration ratios, percentiles, and distributions
- **Data quality:** Handled nulls, duplicates, and many-to-many joins with proper deduplication

### Data Visualisation Skills

- **Tableau LOD calculations:** Created `True GMV` field to deduplicate many-to-many payments before aggregation
- **Table calculations:** Built running totals, cumulative percentages, and window aggregations
- **Lorenz curve:** Constructed a technically accurate Pareto distribution using 8 custom calculated fields
- **Geographic mapping:** Converted state codes to filled maps showing regional patterns
- **Dashboard design:** Combined 7 visualisations into a coherent business narrative

### Communication Skills

- **STAR documentation:** Every analysis phase follows Situation–Task–Action–Result structure
- **Technical precision:** All formulas documented with data types, business logic, and examples
- **Narrative flow:** 8 documents build logically from problem diagnosis through to recommendations
- **Stakeholder-appropriate writing:** Different sections target different audiences (executives vs. analysts)

### Frameworks Applied

| Framework | Where Used |
|---|---|
| **STAR** (Situation–Task–Action–Result) | Analysis documentation |
| **RACI** (Responsible–Accountable–Consulted–Informed) | Stakeholder classification |
| **Nadler-Tushman Congruence Model** | Root cause diagnosis (Work, People, Structure, Culture) |
| **AS-IS vs. TO-BE** | Gap quantification |
| **Pareto Principle** (80/20 Rule) | Seller concentration analysis |
| **6P Framework** | Problem diagnosis before data |
| **MoSCoW** | Recommendation prioritisation |

### Tools Used

- **Excel** (Power Query, XLOOKUP, Pivot Tables, Calculated Columns) — Data consolidation, transformation, and aggregation
- **Tableau Desktop** (LOD Calculations, Table Calculations, Geographic Mapping) — Dashboard visualisation and Pareto analysis
- **draw.io** (BPMN, Power/Interest Grid, Database Schema) — Process mapping and stakeholder analysis

---

## Dataset & Repository

**Dataset:** Olist Brazilian E-Commerce Public Dataset | [Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce/data) | [Olist Website](https://olist.com/ecommerce/)

| | |
|---|---|
| **Time Period** | September 2016 – August 2018 |
| **Orders Analysed** | 96,478 delivered orders (97% of dataset) |
| **Sellers** | 2,960 unique sellers |
| **Customers** | 99,441 unique customers |
| **Geographic Coverage** | All 27 Brazilian states |
| **Analysis Time** | ~40 hours (problem diagnosis → final recommendations) |
| **Documentation** | 9 markdown files (15,000+ words) |
| **Visualisations** | 13 images + 1 Tableau workbook |
| **Analysis Artefacts** | 23 Excel formulas + 8 Tableau calculated fields |

**Why this dataset:** Real production data from a live Brazilian marketplace — not synthetic. Covers the complete order lifecycle (purchase → delivery → review) across 9 relational CSV files, requiring data engineering before any analysis could begin.

```
olist-analysis/
├── dashboard/
│   └── Olist_Analysis_Dashboard.pptx
├── data/
│   ├── raw_data/
│   │   └── README.md                       (Points to Kaggle source)
│   ├── Olist_Business_Analysis.xlsx        (Excel analysis workbook)
│   └── Olist_Analysis_Dashboard__2.twb     (Tableau workbook)
├── images/
│   ├── database_schema.png                 (Physical ERD created by analyst)
│   ├── erd_olist_kaggle.png                (Original ERD from Kaggle dataset)
│   ├── bpmn_process_map.png               (AS-IS order fulfilment process)
│   ├── stakeholder_map.png                 (Power/Interest Grid)
│   ├── customers_by_state.png              (Geographic map)
│   ├── sellers_by_state.png                (Geographic map)
│   ├── h1_delay_severity_vs_score.png
│   ├── h2_revenue_by_state.png
│   ├── h3_gmv_pareto_distribution.png      (Lorenz curve)
│   ├── h3_seller_concentration_kpi.png     (KPI card)
│   ├── h4_freight_by_state.png
│   ├── monthly_growth.png
│   └── dashboard_full_view.png
├── 1-business-problem-diagnosis.md
├── 2-stakeholder-map.md
├── 3-current-state.md
├── 4-analysis.md
├── 5-gap-analysis.md
├── 6-insights.md
├── 7-business-recommendations.md
├── 8-data-dictionary.md
└── README.md
```

---

**Analyst:** Varneet Singh | [LinkedIn](https://www.linkedin.com/in/varneet-singh/) | [Portfolio](https://varneet-s.github.io/varneet-portfolio) | [Email](mailto:varneetsingh45@gmail.com)

**Analysis Date:** May 2026 | **Dataset Period:** September 2016 – August 2018
