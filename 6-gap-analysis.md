# Gap Analysis

## Purpose

Gap analysis quantifies the distance between the current state (AS-IS) and the desired future state (TO-BE). This document identifies measurable performance gaps across three dimensions—freight cost, delivery performance, and geographic revenue distribution—and applies the Nadler-Tushman Congruence Model to diagnose root causes.

---

## Gap Framework: AS-IS vs. TO-BE

| Performance Metric | AS-IS (2016-2018) | TO-BE (Target) | Gap | Priority |
|---|---|---|---|---|
| **Freight Cost % (Northern States)** | 50-60% | <20% | -30 to -40 percentage points | High |
| **Avg Review Score (Late Deliveries)** | 2.27 | >3.5 | +1.23 points | High |
| **Revenue Concentration (SP)** | 42% | <25% | -17 percentage points | Medium |
| **Seller Distribution (Northern States)** | <2% of sellers | >10% of sellers | +8 percentage points | Medium |
| **On-Time Delivery Rate (Remote Routes)** | ~93% (platform-wide) | >97% | +4 percentage points | High |

---

## Gap 1: Freight Cost Burden in Northern States

### AS-IS Performance
Customers in Roraima (RR), Rondônia (RO), Maranhão (MA), and Acre (AC) paid freight costs exceeding 50% of product price. For a R$100 product, customers in RR paid R$60 in freight, making the total cost R$160. In São Paulo, the same product cost R$125 (R$100 + R$25 freight).

**Quantified Impact:**
- RR: 60.07% avg freight burden (46 orders)
- RO: 57.83% avg freight burden (253 orders)
- MA: 53.67% avg freight burden (747 orders)
- SP baseline: 25.24% avg freight burden

### TO-BE Target
Reduce freight as a percentage of product price to below 20% in all states, matching industry benchmarks for domestic e-commerce logistics in Brazil.

### Gap Magnitude
Northern states need a **30-40 percentage point reduction** in freight burden to reach competitive parity with São Paulo. This translates to cutting freight costs by 50-60% in absolute terms for remote-region orders.

### Why This Gap Exists
- Long distances from SP-based sellers to northern customers (2,000-3,000 km)
- Sparse carrier infrastructure in northern states (fewer distribution centers, limited last-mile capacity)
- Low order volume per route reduces carrier efficiency (trucks running half-empty)

---

## Gap 2: Delivery Performance & Customer Satisfaction

### AS-IS Performance
Late deliveries (orders arriving after the estimated delivery date) occurred in 6,534 out of 96,478 delivered orders (~6.8% late rate). However, the **satisfaction impact was disproportionate**:
- Late deliveries: 2.27 avg review score
- On-time deliveries: 4.03 avg review score
- Gap: **1.76 points**

Orders 7+ days late averaged **1.70 review scores**, functionally destroying customer retention potential.

### TO-BE Target
- Reduce late delivery rate to <3% platform-wide
- Improve avg review score for late deliveries to >3.5 (through faster recovery processes, proactive communication)
- Achieve >4.0 avg review score across all delivery statuses

### Gap Magnitude
- Late delivery rate must drop by **~4 percentage points** (from 6.8% to <3%)
- Review scores for late orders must improve by **+1.23 points** (from 2.27 to 3.5)

### Why This Gap Exists
- Estimated delivery dates do not account for actual transit time variability in remote regions
- No priority routing or expedited handling for high-risk routes
- Sellers lack visibility into carrier performance, cannot adjust packing speed accordingly

---

## Gap 3: Geographic Revenue Concentration

### AS-IS Performance
São Paulo generated 42% of total platform revenue (R$4.62M out of R$12.09M). The top three states (SP, RJ, MG) accounted for ~70% of GMV. Northern and central-west states combined contributed less than 15% of revenue despite representing significant population and purchasing power.

**Order distribution mismatch:**
- Customers distributed across all 27 states
- Sellers concentrated in 4 states (SP: 1,764 sellers, MG: 233, PR: 334, RJ: 162)

### TO-BE Target
Diversify revenue generation so that no single state exceeds 25% of platform GMV. Increase northern/central-west contribution to >30% of total revenue.

### Gap Magnitude
São Paulo revenue share must decline by **~17 percentage points** (from 42% to 25%). This doesn't mean reducing absolute revenue from SP—it means growing revenue in other states faster than SP grows.

Northern states need to increase their collective contribution by **+15 percentage points** (from ~15% to 30%).

### Why This Gap Exists
- Seller supply concentrated in southeast (network effects: sellers attract customers, customers attract sellers)
- High freight costs suppress demand in remote regions (customers abandon carts when they see 50-60% freight burden)
- No targeted seller acquisition campaigns for underserved states

---

## Root Cause Diagnosis: Nadler-Tushman Congruence Model

The Nadler-Tushman framework diagnoses organizational performance by examining four components: **Work, People, Structure, and Culture**. Gaps arise when these components are misaligned.

### Component 1: Work (Processes & Workflows)

**Current State:**
The order fulfillment workflow is optimized for same-region or short-distance deliveries (SP seller → SP customer). The same process applies to cross-country deliveries (SP seller → RR customer), but it doesn't account for:
- Longer transit times requiring buffer adjustments
- Higher risk of delays requiring proactive customer communication
- Different carrier partnerships needed for remote routes

**Misalignment:**
Work processes assume geographic proximity. When distance increases, the workflow breaks down (late deliveries, high freight).

**Required Change:**
Introduce regional process variants—different estimated delivery windows, dedicated carrier agreements, and priority seller matching for remote orders.

---

### Component 2: People (Skills & Expertise)

**Current State:**
Olist's operations team during 2016-2018 lacked dedicated logistics expertise for long-haul or northern-region fulfillment. Most team members understood southeast e-commerce dynamics but had no experience negotiating regional carrier contracts or managing remote-route optimization.

**Misalignment:**
The people responsible for delivery performance lack the specialized knowledge required to solve northern-state logistics challenges.

**Required Change:**
Hire or train logistics specialists with expertise in remote-region fulfillment and carrier network design outside the southeast.

---

### Component 3: Structure (Organizational Design)

**Current State:**
Olist operated without a dedicated logistics function during this period. Carrier relationships were managed reactively by the operations team, with no clear ownership of:
- Route optimization
- Freight cost negotiation
- Delivery performance monitoring by region

**Misalignment:**
The organizational structure lacks a function responsible for solving the freight and delivery gaps. Without ownership, problems persist.

**Required Change:**
Create a Logistics & Regional Expansion team with clear accountability for freight cost reduction, carrier partnerships in underserved regions, and delivery performance targets by state.

---

### Component 4: Culture (Values & Norms)

**Current State:**
Growth during 2016-2018 was driven by expanding seller count and order volume in established markets (São Paulo, Rio, Minas Gerais). The implicit cultural norm was "grow where it's easy." Northern states were deprioritized because they were harder to serve and represented smaller immediate revenue.

**Misalignment:**
The culture prioritizes short-term efficiency (maximize orders in SP) over long-term market diversification (invest in remote-region infrastructure).

**Required Change:**
Shift cultural focus toward geographic diversification as a strategic priority. Measure success by "revenue per state" and "freight equity" rather than just total GMV.

---

## Congruence Diagnosis Summary

| Gap | Root Cause (Nadler-Tushman) | Affected Component |
|---|---|---|
| High freight costs in northern states | Workflow designed for short distances + no logistics function | Work + Structure |
| Late deliveries causing review score collapse | No regional process variants + no proactive communication protocols | Work |
| Revenue concentration in São Paulo | Growth culture focused on easy markets + no dedicated expansion team | Culture + Structure |
| Seller shortage in remote regions | No targeted acquisition strategy + no expertise in remote-region seller support | People + Structure |

---

## Priority Ranking

Based on the magnitude of impact and urgency:

1. **Freight Cost Gap** (High Priority) — Directly suppresses demand in 40% of Brazilian states. Solving this unlocks latent revenue.
2. **Delivery Performance Gap** (High Priority) — Late deliveries are destroying customer retention. Even small improvements (reducing 7+ day delays) yield large satisfaction gains.
3. **Revenue Concentration Gap** (Medium Priority) — Critical for long-term sustainability but less urgent than operational crises (freight/delivery).

---

## Implications for Recommendations

The gaps identified here are **not independent**—they are causally linked:
- High freight costs exist **because** sellers are concentrated in SP
- Late deliveries occur **because** the fulfillment workflow doesn't account for distance
- Revenue concentration persists **because** customers in remote regions face high freight and poor delivery performance

**Therefore**, recommendations must address the underlying structural causes (logistics function, regional carrier partnerships, seller diversification) rather than treating symptoms (subsidizing freight without fixing the process).

Detailed recommendations are provided in [Business Recommendations](./business-recommendations.md).
