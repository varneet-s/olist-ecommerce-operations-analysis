# Business Problem

## Organization Background

Olist is a Brazilian e-commerce marketplace aggregator that connects small and medium-sized sellers to major online platforms like Mercado Livre, B2W, and Via Varejo. Instead of managing contracts with multiple marketplaces separately, sellers pay Olist a single fee to list their products across all platforms under one consolidated agreement. Olist handles the marketplace relationships while sellers fulfill orders directly from their own locations.

The dataset covers approximately 99,000 orders placed between 2016 and 2018 across Brazil's 27 states.

## Problem Statement

Olist faced a structural geographic concentration problem during the 2016–2018 period. Revenue, seller supply, and order volume were heavily concentrated in São Paulo and the surrounding southeast states, while northern and remote regions remained significantly underserved. This concentration created three interrelated business risks:

1. **Freight Cost Burden**: Customers in remote states like Roraima (RR), Rondônia (RO), and Maranhão (MA) were paying disproportionately high freight costs relative to product prices—often exceeding 50-60% of the order value compared to ~30% in São Paulo.

2. **Delivery Performance Failures**: Late deliveries were causing severe customer satisfaction collapse. Orders arriving late averaged review scores of 2.27 compared to the platform average of 4.03, a gap of 1.76 points that threatened repeat purchase behavior and platform reputation.

3. **Revenue Concentration Risk**: São Paulo alone accounted for approximately 42% of total platform revenue, with the top three states generating roughly 70% of GMV. This over-reliance on the southeast created structural vulnerability and left untapped market potential across the rest of Brazil.

## Business Impact

The gaps identified above had direct consequences:

- **Customer Churn Risk**: Low satisfaction scores from late deliveries reduced the likelihood of repeat purchases and positive word-of-mouth referrals.
- **Limited Market Penetration**: Insufficient seller density outside São Paulo meant customers in northern states had fewer product choices and longer delivery times, suppressing demand growth.
- **Revenue Volatility**: Heavy dependence on three states exposed the platform to regional economic shocks and competitive pressure in established markets.

## Scope of Analysis

This analysis focused on understanding the scale, distribution, and root causes of these three gaps using delivered orders only (~96,000 records representing 97% of the dataset). The objective was to provide Olist's leadership with data-backed evidence to inform decisions on:

- Geographic expansion strategy
- Seller acquisition priorities by region
- Logistics optimization investments
- Delivery performance improvement initiatives

## Analytical Questions (Hypotheses)

Before touching the data, I formed four hypotheses to guide the analysis:

**H1: Late deliveries are the biggest driver of low review scores**  
Prediction: Delivery timing directly impacts customer satisfaction, with late orders receiving significantly worse reviews than on-time or early deliveries.

**H2: São Paulo dominates revenue — the rest of Brazil is underserved**  
Prediction: Revenue and order volume are heavily concentrated in SP and nearby states, while northern and remote regions contribute minimal GMV despite potential latent demand.

**H3: Top 20% of sellers generate the majority of GMV (Pareto Principle)**  
Prediction: A small subset of high-performing sellers accounts for a disproportionate share of total platform revenue, following the 80/20 rule.

**H4: Freight cost as a percentage of product price is much higher in northern states**  
Prediction: Customers in remote regions pay significantly more in freight relative to their order value compared to customers in São Paulo and the southeast.

---

**Next Steps**: These hypotheses were tested through structured data analysis using Excel pivot tables and Tableau visualizations. Results are documented in the [Analysis](./analysis.md) and [Insights](./insights.md) sections.
