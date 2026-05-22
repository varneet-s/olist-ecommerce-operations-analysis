# Hypotheses

## Hypothesis-Driven Analysis

Before opening the dataset or running any analysis, I formed four business hypotheses based on Olist's operating model and the structural challenges facing marketplace aggregators in geographically diverse markets. This approach kept the analysis purposeful—testing specific predictions rather than browsing data randomly.

---

## H1: Late Deliveries Are the Biggest Driver of Low Review Scores

**Hypothesis**: Delivery timing directly impacts customer satisfaction. Orders that arrive late will receive significantly worse review scores compared to on-time or early deliveries.

**Business Logic**: In e-commerce, unmet delivery expectations erode trust. If a customer expects a package on Tuesday and it arrives on Friday, the product quality becomes secondary to the frustration of waiting.

**Test Method**: Compare average review scores across delivery status categories (Early, On Time, Late) and severity bands (Late 1-3 days, Late 4-7 days, Late 7+ days).

**Result**: ✅ **Confirmed**. Late deliveries averaged 2.27 vs. 4.03 for on-time orders. Review scores collapsed progressively as delay severity increased—from 4.30 (early) down to 1.70 (7+ days late).

---

## H2: São Paulo Dominates Revenue — The Rest of Brazil Is Underserved

**Hypothesis**: Revenue and order volume are heavily concentrated in São Paulo and the surrounding southeast states, while northern and remote regions contribute minimal GMV despite potential latent demand.

**Business Logic**: Olist's seller base grew organically in São Paulo, Brazil's economic center. This creates a network effect—more sellers in SP attract more customers in SP, while remote states remain underserved due to insufficient seller density.

**Test Method**: Calculate total revenue (sum of price) by customer state and identify the percentage contribution of the top states. Build geographic maps showing customer vs. seller distribution.

**Result**: ✅ **Confirmed**. São Paulo accounted for ~42% of total platform revenue (R$4.62M out of R$12.09M). The top three states (SP, RJ, MG) generated approximately 70% of GMV. Geographic maps revealed a clear mismatch: customers spread across all 27 states, sellers concentrated in the southeast.

---

## H3: Top 20% of Sellers Generate the Majority of GMV (Pareto Principle)

**Hypothesis**: A small subset of high-performing sellers accounts for a disproportionate share of total platform revenue, following the 80/20 rule commonly observed in marketplace economics.

**Business Logic**: Not all sellers are created equal. A few professional sellers with optimized logistics, better inventory, and competitive pricing will naturally capture most of the order volume.

**Test Method**: Rank all sellers by total revenue (sum of price), calculate the revenue contribution of the top 20% (592 out of 2,960 sellers), and visualize the concentration using a Lorenz curve (GMV Pareto Distribution).

**Result**: ✅ **Confirmed**. The top 20% of sellers (592 sellers) generated 82.54% of total platform GMV. This extreme concentration indicates that Olist's revenue health depends heavily on retaining and supporting its top-performing sellers.

---

## H4: Freight Cost as a Percentage of Product Price Is Much Higher in Northern States

**Hypothesis**: Customers in remote northern regions (Roraima, Rondônia, Amazonas, Maranhão) pay significantly more in freight relative to their order value compared to customers in São Paulo and the southeast.

**Business Logic**: Brazil's logistics infrastructure is concentrated in the southeast. Shipping to remote states involves longer distances, fewer carrier options, and higher per-kilometer costs. This freight burden makes products effectively more expensive for customers in underserved regions.

**Test Method**: Calculate `freight_pct = (freight_value / price) * 100` for each order, then compute the average freight percentage by customer state.

**Result**: ✅ **Confirmed**. Northern states had freight costs exceeding 50% of product price:
- Roraima (RR): 60.07%
- Rondônia (RO): 57.83%
- Maranhão (MA): 53.67%
- São Paulo (SP): ~25% (baseline comparison)

Customers in remote states were paying double the freight burden relative to their purchase value.

---

## Hypothesis Not Pursued

**H5: Certain product categories have structurally worse satisfaction scores**  
This hypothesis was dropped during scoping because it added unnecessary complexity without addressing the core geographic and operational gaps. The analysis stayed focused on delivery performance, seller concentration, and regional distribution.

---

**Outcome**: All four hypotheses were confirmed through structured pivot table analysis and Tableau visualizations. The findings validated the initial business intuition and provided measurable evidence for strategic decision-making. Detailed test results and methodologies are documented in [Analysis](./analysis.md) and [Insights](./insights.md).
