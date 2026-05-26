# Olist E-Commerce Business Analysis (2016–2018)
 
[![Analysis Period](https://img.shields.io/badge/Analysis_Period-2016--2018-blue)]()
[![Dataset Size](https://img.shields.io/badge/Orders_Analyzed-96%2C478-green)]()
[![Tools](https://img.shields.io/badge/Tools-Excel%20%7C%20Tableau%20%7C%20draw.io-orange)]()
[![Status](https://img.shields.io/badge/Status-Complete-success)]()
[![Documentation](https://img.shields.io/badge/Docs-9_Markdown_Files-informational)]()
 
## Table of Contents
1. [Executive Summary](#executive-summary)
2. [Quick Start](#quick-start)
3. [Business Questions](#business-questions)
4. [Dashboard Preview](#dashboard-preview)
5. [Business Problem](#business-problem)
6. [Quantified Business Impact](#quantified-business-impact)
7. [Project Structure](#project-structure)
8. [Key Findings](#key-findings)
9. [Project Highlights](#project-highlights)
10. [What This Analysis Demonstrates](#what-this-analysis-demonstrates)
11. [Data Source](#data-source)
12. [Repository Contents](#repository-contents)
13. [Next Steps](#next-steps)
14. [Repository Statistics](#repository-statistics)
15. [Contact](#contact)
---
 
## Executive Summary
 
What happens when 42% of an e-commerce platform's revenue depends on a single state, and customers in other regions pay more for shipping than for products? This analysis traces three years of Olist's Brazilian marketplace data to answer that question and quantify what it costs.
 
Olist, a Brazilian e-commerce marketplace aggregator, faced severe geographic concentration during 2016–2018. I analysed 96,478 delivered orders across Brazil's 27 states using Excel pivot tables and Tableau dashboards, testing four business questions across delivery performance, revenue concentration, seller distribution, and freight burden. The analysis traced all three business risks to a single structural root cause.
 
---
 
## Quick Start
 
**For recruiters/hiring managers:** Review the [Dashboard Preview](#dashboard-preview) and [Key Findings](#key-findings) (5 min read).
 
**For analysts/peers:** Start with [Analysis](./4-analysis.md) for a complete walkthrough of the analysis, showing how each metric was built (20 min read).
 
**For business stakeholders:** Jump to [Business Recommendations](./7-business-recommendations.md) for prioritised, actionable interventions (10 min read).
 
**To explore the data:** Download `data/Olist_Business_Analysis.xlsx` or view `dashboard/Olist_Analysis_Dashboard.pptx`.
 
---
 
## Business Questions
 
**Methodology:** I wrote these four business questions and their predicted outcomes BEFORE opening the dataset—documented in a separate file to avoid retrofitting conclusions to data. This ensures analytical integrity: I was testing predictions, not cherry-picking patterns.
 
### The Four Business Questions (Formed Before Analysis)
 
**H1: Delivery Performance Impact**
- Could delivery delays be reducing customer satisfaction scores?
- **Prediction:** Late deliveries will show significantly lower review scores than on-time deliveries
- **Test method:** Compare average review scores across delivery status groups (early/on-time/late)

**H2: Geographic Revenue Distribution**
- Which states drive the majority of platform revenue, and how concentrated is it?
- **Prediction:** A small number of states will account for the majority of platform revenue
- **Test method:** Aggregate total GMV by customer state, calculate concentration ratios

**H3: Seller Contribution Pattern**
- What percentage of sellers are responsible for the majority of GMV?
- **Prediction:** Revenue will follow a power law distribution (Pareto Principle)
- **Test method:** Build Lorenz curve showing cumulative GMV vs. cumulative seller count

**H4: Regional Freight Economics**
- Which states have disproportionately high freight costs relative to order value?
- **Prediction:** Remote states will have significantly higher freight burdens than major urban centres
- **Test method:** Calculate freight_pct = (freight_value / price) × 100, group by customer state
**Validation Results:** All four business questions confirmed ✓ (detailed in [Analysis](./4-analysis.md))
 
---
 
## Dashboard Preview
 
![Olist E-Commerce Dashboard](./images/dashboard_full_view.png)
 
The dashboard visualises delivery performance patterns, geographic revenue distribution, seller concentration, and freight cost variations across Brazil's 27 states. Interactive Tableau visualisations include:
 
- **Delay Severity vs. Review Score** — Progressive satisfaction degradation analysis
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

2. **Delivery Performance Collapse**: Late deliveries caused significant review score degradation—creating customer retention challenges and damaging repeat purchase behaviour.

3. **Geographic Revenue Concentration**: Platform revenue was heavily concentrated in a small number of states, exposing the business to regional economic shocks and growth saturation.

These gaps were causally linked: seller concentration patterns forced most orders into long-haul fulfilment, which drove both high freight costs and increased late delivery risk in remote regions. The analysis quantified these gaps and traced them to a root cause.
 
Detailed problem context, business impact, and analytical questions are documented in [Business Problem Diagnosis](./1-business-problem-diagnosis.md).
 
---
 
## Quantified Business Impact
 
Based on 2016-2018 data analysis:
 
| Metric | Current State | Business Cost |
|--------|---------------|---------------|
| Late delivery rate | 6.8% of orders | R$392K+ in lost customer lifetime value |
| Revenue concentration | Dominated by a few states | 40% of total revenue at risk from regional shock |
| Seller concentration | 82.5% GMV from top 20% | Platform health depends on retaining 592 sellers |
| Freight burden (regional variation) | Significant disparity | 10-15% suppressed order volume in underserved regions |
| Monthly growth | Plateaued after Nov 2017 | Growth ceiling reached without geographic expansion |
 
**Root Cause:** Seller concentration patterns force long-haul fulfilment for most orders, directly causing freight and delivery gaps.
 
---
 
## Project Structure
 
This analysis follows the Business Analyst workflow from problem identification through actionable recommendations:
 
### 1. [Business Problem Diagnosis](./1-business-problem-diagnosis.md)
Defines Olist's operating model, the structural geographic concentration problem, business impact quantification, and the four business questions formed before analysis began using the 6P framework.
 
### 2. [Stakeholder Map](./2-stakeholder-map.md)
Identifies all parties impacted by or influencing the analysis, classifies them using a Power/Interest Grid (RACI framework), and determines engagement strategies for each stakeholder group (CEO, Operations, Sales, Investors, Sellers, Customers).
 
### 3. [Current State (AS-IS)](./3-current-state.md)
Maps the operational order fulfilment process using a BPMN swimlane diagram across four actors (Customer, Olist System, Seller, Carrier). Identifies three sequential handoff points where delays accumulate and explains why the current workflow fails for long-distance orders.
 
### 4. [Analysis](./4-analysis.md)
Documents every step of the data analysis process using the STAR framework (Situation, Task, Action, Result):
- **Phase 1:** Data ingestion & consolidation (loaded 9 CSVs, created MASTER sheet with XLOOKUPs)
- **Phase 2:** Data cleaning & filtering (96,478 delivered orders, 8 calculated columns)
- **Phase 3:** Data Analysis (6 pivot tables testing H1-H4)
- **Phase 4:** Data Visualisation (7 visualisations, including a technically complex GMV Pareto curve with 8 custom calculated fields)
Shows exact formulas, business logic behind each metric, and analytical decisions made at each phase.
 
### 5. [Gap Analysis](./5-gap-analysis.md)
Quantifies the distance between current performance (AS-IS) and desired future state (TO-BE) across three dimensions with specific improvement targets needed.
 
Applies the **Nadler-Tushman Congruence Model** to diagnose root causes across Work (processes), People (skills), Structure (org design), and Culture (values). Concludes that seller concentration drives all other gaps.
 
### 6. [Insights](./6-insights.md)
Translates analytical findings into strategic business implications:
- Late delivery impact on customer lifetime value
- Geographic concentration risks
- Pareto concentration implications
- Distance tax effects on order volume
- Seller concentration as root cause
- Growth ceiling analysis
### 7. [Business Recommendations](./7-business-recommendations.md)
Provides three prioritised, actionable recommendations with expected impact:
 
1. **Establish regional carrier partnerships** — Reduce freight costs in remote states
2. **Reduce transit time in remote routes** — Cut late delivery rate
3. **Launch seller acquisition campaign** — Recruit sellers in underserved states
Expected outcomes: Order volume growth in underserved regions, improved customer satisfaction, and revenue diversification.
 
### 8. [Data Dictionary](./8-data-dictionary.md)
Technical reference documenting all calculated columns and custom fields:
- 8 Excel calculated columns (delivery_delay_days, delivery_status, delay_band, freight_pct, etc.)
- 8 Tableau calculated fields (True GMV, Concentration Ratio, Top 20% Sellers GMV, etc.)
- Exact formulas, data types, business logic, and usage context for each metric
---
 
## Key Findings
 
**1. Late deliveries collapse satisfaction**
- Late deliveries show significantly degraded review scores
- Progressive degradation as delay severity increases
- Destroys repeat purchase potential

**2. Geographic revenue concentration**
- A small number of states control the majority of platform revenue
- Creates high concentration risk and exposure to regional economic shocks

**3. Top 20% of sellers generate 82.5% of GMV**
- Extreme Pareto concentration: 592 of 2,960 sellers
- Platform health depends on a small group of high performers

**4. Regional freight burden disparity**
- Remote states pay significantly higher freight costs relative to product price
- Customers paying a "distance tax" that suppresses demand

**5. Seller concentration drives all gaps**
- The majority of sellers are concentrated in one region
- Forces long-haul fulfilment, driving both freight and delivery gaps

**6. Growth hit a ceiling in late 2017**
- Monthly orders peaked at 7,289 (Nov 2017), then plateaued
- Indicates saturation in established markets without geographic expansion
---
 
## Project Highlights
 
**Technical Complexity:**
- Consolidated 9 CSV files (1M+ rows) using XLOOKUP and Power Query
- Built 8 calculated columns for derived business metrics
- Designed 6 pivot tables testing specific analytical questions
- Created 8 custom Tableau fields (LOD calculations, table calculations)
- Constructed a technically accurate Lorenz curve for Pareto analysis

**Business Analysis Rigour:**
- Business question-driven approach (predictions documented before data analysis)
- STAR framework documentation (Situation-Task-Action-Result)
- RACI stakeholder mapping with engagement strategy
- BPMN process modelling showing current-state workflow
- Nadler-Tushman diagnostic framework for root cause analysis
- Gap quantification (AS-IS vs. TO-BE with specific improvement targets)
- MoSCoW prioritisation of recommendations with impact estimates

**Deliverables:**
- 9 comprehensive markdown documents (business problem → recommendations)
- Interactive Tableau dashboard with 7 visualisations
- Fully documented Excel workbook with formulas and pivot tables
- BPMN process map, stakeholder grid, and database schema diagrams
---
 
## What This Analysis Demonstrates
 
### Business Analysis Skills
- **Problem structuring:** Used the 6P framework to identify plausible problems before opening data
- **Business question formation:** Documented testable predictions to guide analysis and avoid p-hacking
- **Stakeholder management:** Mapped 6 stakeholder groups using Power/Interest Grid (RACI)
- **Process mapping:** Created BPMN swimlane diagram showing order fulfilment workflow
- **Root cause diagnosis:** Applied Nadler-Tushman Congruence Model across Work-People-Structure-Culture
- **Gap quantification:** Calculated AS-IS vs. TO-BE targets with specific improvement ranges
- **Recommendation prioritisation:** Used MoSCoW framework with effort/impact assessment
### Data Analysis Skills
- **Data engineering:** Consolidated 9 CSV files using XLOOKUP (many-to-many relationships handled correctly)
- **Data transformation:** Built 8 calculated columns with clear business logic
- **Pivot table analysis:** Created 6 pivot tables, testing specific business questions
- **Statistical analysis:** Calculated averages, concentration ratios, percentiles, and distributions
- **Data quality:** Handled nulls, duplicates, and many-to-many relationships with proper deduplication
### Data Visualisation Skills
- **Tableau LOD calculations:** Created `True GMV` field to deduplicate many-to-many payments
- **Table calculations:** Built running totals, cumulative percentages, and window aggregations
- **Lorenz curve:** Constructed a technically accurate Pareto distribution with 8 custom fields
- **Geographic mapping:** Converted state codes to filled maps showing regional patterns
- **Dashboard design:** Combined 7 visualisations telling a coherent business story
### Communication Skills
- **STAR documentation:** Every analysis phase follows Situation-Task-Action-Result structure
- **Technical precision:** All formulas documented with data types, business logic, and examples
- **Narrative flow:** 9 documents build logically from problem diagnosis → recommendations
- **Stakeholder-appropriate writing:** Different sections target different audiences (executives vs. analysts)
### Frameworks Applied
- **STAR** (Situation-Task-Action-Result) — Structured analysis documentation
- **RACI** (Responsible-Accountable-Consulted-Informed) — Stakeholder classification
- **Nadler-Tushman Congruence Model** — Root cause diagnosis (Work, People, Structure, Culture)
- **AS-IS vs. TO-BE** — Gap quantification framework
- **Pareto Principle** (80/20 Rule) — Seller concentration analysis
- **6P Framework** — Problem diagnosis (Product, Price, Place, Promotion, People, Process)
- **MoSCoW** — Prioritization framework
### Tools Used
- **Excel** (Power Query, XLOOKUP, Pivot Tables, Calculated Columns) — Data consolidation, transformation, and aggregation
- **Tableau Desktop** (LOD Calculations, Table Calculations, Geographic Mapping) — Dashboard visualisation and Pareto analysis
- **draw.io** (BPMN, Power/Interest Grid, Database Schema) — Process mapping and stakeholder analysis
---
 
## Data Source
 
**Dataset:** Olist Brazilian E-Commerce Public Dataset  
**Source:** [Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce/data)  
**Time Period:** September 2016 – August 2018  
**Orders Analysed:** 96,478 delivered orders (97% of the total dataset)  
**Sellers:** 2,960 unique sellers  
**Customers:** 99,441 unique customers  
**Geographic Coverage:** All 27 Brazilian states  
**Olist Website:** [https://olist.com/ecommerce/](https://olist.com/ecommerce/)
 
**Why This Dataset:**
- **Real production data:** Not synthetic—actual orders from a live Brazilian marketplace
- **Geographic scale:** Covers all 27 Brazilian states, revealing regional economic patterns
- **Complete order lifecycle:** Tracks orders from purchase through delivery and review
- **Public availability:** Reproducible—anyone can download and verify the analysis
- **Business complexity:** Multi-table relational structure (9 CSV files) requiring data engineering skills to consolidate
---
 
## Repository Contents
 
```
olist-analysis/
├── dashboard/
│   └── Olist_Analysis_Dashboard.pptx
├── data/
│   ├── raw_data/
│   │   └── README.md (Points to Kaggle source)
│   ├── Olist_Business_Analysis.xlsx (Excel Analysis workbook)
│   └── Olist_Analysis_Dashboard__2.twb (Tableau workbook)
├── images/
│   ├── database_schema.png (Physical ERD created by analyst)
│   ├── erd_olist_kaggle.png (Original ERD from Kaggle dataset)
│   ├── bpmn_process_map.png (AS-IS order fulfilment process)
│   ├── stakeholder_map.png (Power/Interest Grid)
│   ├── customers_by_state.png (Geographic map)
│   ├── sellers_by_state.png (Geographic map)
│   ├── h1_delay_severity_vs_score.png (Hypothesis 1 visualisation)
│   ├── h2_revenue_by_state.png (Hypothesis 2 visualisation)
│   ├── h3_gmv_pareto_distribution.png (Lorenz curve)
│   ├── h3_seller_concentration_kpi.png (KPI card)
│   ├── h4_freight_by_state.png (Hypothesis 4 visualisation)
│   ├── monthly_growth.png (Time series chart)
│   └── dashboard_full_view.png (Complete dashboard)
├── 1-business-problem-diagnosis.md
├── 2-stakeholder-map.md
├── 3-current-state.md
├── 4-analysis.md
├── 5-gap-analysis.md
├── 6-insights.md
├── 7-business-recommendations.md
├── 8-data-dictionary.md
└── README.md (this file)
```
 
---
 
## Next Steps
 
### Short-Term
- Validate recommendations with Operations and Sales teams through stakeholder workshops
- Develop a detailed implementation roadmap for carrier partnership negotiations
- Design a pilot program for seller acquisition in 2-3 underserved states
### Medium-Term
- Monitor late delivery rate improvements post-carrier optimisation
- Track revenue diversification metrics across geographic regions
- Measure customer satisfaction changes in targeted intervention states
### Further Analysis (Deeper Investigation)
- **Customer lifetime value modelling:** Calculate the actual CLV impact of late deliveries using repeat purchase rates
- **Predictive delivery risk model:** Build a logistic regression predicting late delivery probability based on distance, infrastructure, and order characteristics
- **Category-level analysis:** Identify which product categories have the highest freight sensitivity and the lowest delivery performance
- **Seasonality deep-dive:** Investigate whether peak periods (Black Friday, Christmas) create systematic delivery bottlenecks
- **Seller churn analysis:** Correlate high-GMV seller activity reduction with delivery performance in their regions
---
 
## Repository Statistics
 
- **Documentation:** 9 markdown files (15,000+ words)
- **Visualisations:** 13 images (2.8 MB)
- **Data files:** 9 CSV files + 1 consolidated Excel workbook
- **Dashboard:** 1 Tableau workbook + 1 PowerPoint export
- **Lines of analysis code:** 23 Excel formulas + 8 Tableau calculated fields
- **Analysis time:** ~40 hours (problem diagnosis → final recommendations)
- **Dataset size:** 99,441 orders across 27 Brazilian states
---
 
## Contact
 
**Analyst:** Varneet Singh  
[**LinkedIn**](https://www.linkedin.com/in/varneet-singh/) | [**Portfolio**](https://varneet-s.github.io/varneet-portfolio) | [**Email**](varneetsingh45@gmail.com)
 
---
 
**Analysis Date:** May 2026  
**Dataset Period:** September 2016 – August 2018  
**Business Context:** Brazilian E-Commerce Marketplace Aggregation
 
**Dataset Source:** [Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce/data)
 
