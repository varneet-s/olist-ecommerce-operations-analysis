# Business Recommendations

## Overview

This document provides three prioritized, actionable recommendations to address the gaps identified in the analysis. Each recommendation includes expected business impact, implementation approach, resource requirements, and success metrics.

---

## Recommendation 1: Establish Regional Carrier Partnerships in Northern States (Priority: High)

### Problem Being Solved
Customers in northern states (RR, RO, MA, AC, PI, AM) pay freight costs exceeding 50% of product price compared to ~25% in São Paulo. This "distance tax" suppresses order volume and makes Olist uncompetitive in 40% of Brazilian states.

### Recommended Action
Negotiate direct partnerships with regional carriers who specialize in northern and central-west routes. Instead of relying on national carriers (Correios, Jadlog) to handle all deliveries, contract with carriers who have established infrastructure in underserved regions. Examples: Rodonaves (strong in northern routes), Expresso Nepomuceno (Amazonas specialist).

**Key Partnership Terms:**
- Volume-based pricing discounts (minimum 500 orders/month per state)
- Guaranteed delivery windows (max 10 days for remote states)
- Co-investment in last-mile infrastructure (Olist subsidizes distribution center setup in exchange for preferential rates)

### Expected Business Impact

**Freight Cost Reduction:**
- Target: Reduce freight as % of price from 50-60% to <30% in northern states
- This makes Olist's effective pricing competitive with regional competitors

**Order Volume Growth:**
- Conservative estimate: 15% order volume increase in northern states once freight burden drops
- Current northern orders: ~1,500/year → projected increase: +225 orders/year
- Average order value: R$125 → additional annual GMV: R$28,125

**Customer Satisfaction Improvement:**
- Freight is the #1 customer complaint in remote regions
- Solving this improves NPS and reduces churn

### Implementation Approach

**Phase 1: Carrier RFP (Months 1-2)**
- Issue Request for Proposal to 5-7 regional carriers
- Specify volume commitments, rate targets, and delivery SLAs
- Evaluate bids based on cost, coverage, and reliability track record

**Phase 2: Pilot Program (Months 3-4)**
- Select 2 carriers for pilot (one for northern states, one for central-west)
- Route 30% of orders in target states through new carriers
- Monitor delivery times, freight costs, and customer satisfaction

**Phase 3: Full Rollout (Months 5-6)**
- Scale winning carrier partnerships to 100% of eligible orders
- Renegotiate contracts with national carriers to focus on southeast routes where they're most efficient

### Resource Requirements
- **Budget**: R$50,000 for pilot subsidies and contract negotiations
- **Headcount**: 1 Logistics Manager (new hire or contractor) to manage partnerships
- **Technology**: Integration with carrier APIs for tracking and rate calculation (existing Olist engineering team, 40 hours of dev work)

### Success Metrics
- Avg freight % in northern states drops from 50-60% to <30% within 6 months
- Delivery time for northern routes reduced by 20% (e.g., 12 days → 9.6 days)
- Order volume in northern states increases by 15% year-over-year

### Risks & Mitigation
- **Risk**: Regional carriers lack capacity for order volume spikes
  - **Mitigation**: Contract with 2 carriers per region for redundancy
- **Risk**: Integration complexity with carrier APIs
  - **Mitigation**: Use Olist's existing carrier integration framework (already supports multiple carriers)

---

## Recommendation 2: Implement Dynamic Delivery Windows for Remote Routes (Priority: High)

### Problem Being Solved
The current fulfillment workflow uses the same estimated delivery date logic for all orders, regardless of distance. This causes:
- Overly optimistic delivery promises for remote-region orders
- Higher late delivery rates (6.8% overall, likely >10% for northern routes)
- Review score collapse when expectations aren't met (late orders: 2.27 avg score)

### Recommended Action
Replace the current static estimated delivery date calculation with a dynamic routing engine that accounts for:
1. Seller location (state)
2. Customer location (state)
3. Historical carrier performance on that specific route
4. Current order volume and carrier capacity

**Example:**
- **Current system**: SP seller → RR customer = "Estimated delivery: 7 days"
- **New system**: SP seller → RR customer = "Estimated delivery: 12 days" (based on actual avg transit time)

This manages customer expectations upfront rather than surprising them with late deliveries.

### Expected Business Impact

**Review Score Improvement:**
- Setting realistic expectations reduces perceived late deliveries
- Target: Improve avg review score for remote-region orders from 3.0 to 3.8
- Every 0.5-point improvement in review score correlates with ~10% increase in repeat purchase rate

**Late Delivery Rate Reduction:**
- Current late rate: 6.8% platform-wide
- Target: Reduce to <3% within 6 months
- Fewer late deliveries = fewer refund requests and customer service escalations

**Operational Efficiency:**
- Reduces customer service volume (fewer "where's my order?" inquiries)
- Estimated savings: 200 fewer support tickets/month → R$6,000/month in support cost reduction

### Implementation Approach

**Phase 1: Data Analysis (Month 1)**
- Calculate average transit time by seller_state → customer_state route
- Identify routes with high late delivery rates (>10%)
- Build baseline delivery time matrix (27 seller states × 27 customer states = 729 route pairs)

**Phase 2: Algorithm Development (Months 2-3)**
- Engineering team builds dynamic estimated delivery date calculator
- Logic: `estimated_date = order_date + route_avg_transit_time + carrier_buffer`
- Integrate with Olist's order processing API

**Phase 3: A/B Test (Month 4)**
- Run split test: 50% of orders use new algorithm, 50% use old system
- Measure late delivery rate, review scores, and customer satisfaction

**Phase 4: Full Rollout (Month 5)**
- Deploy dynamic delivery windows to 100% of orders
- Update marketplace partner integrations to display new delivery estimates

### Resource Requirements
- **Headcount**: 2 engineers × 1 month (existing Olist engineering team)
- **Budget**: R$0 (internal development, no external costs)
- **Data Requirements**: Historical order and delivery data (already available in dataset)

### Success Metrics
- Late delivery rate drops from 6.8% to <3% within 6 months
- Avg review score for remote-region orders improves from 3.0 to 3.8
- Customer service ticket volume related to delivery questions decreases by 30%

### Risks & Mitigation
- **Risk**: Longer estimated delivery times discourage purchases
  - **Mitigation**: Communicate transparently ("We deliver nationwide, including remote areas") and offer expedited options for premium fee
- **Risk**: Route-level data is insufficient for some state pairs (low order volume)
  - **Mitigation**: Fall back to regional averages for low-volume routes until data accumulates

---

## Recommendation 3: Launch Targeted Seller Acquisition Campaign in Underserved States (Priority: Medium)

### Problem Being Solved
59.6% of sellers operate from São Paulo. Northern states combined have <2% of sellers. This seller concentration is the root cause of both the freight gap and the delivery performance gap. Local sellers = shorter shipping distances = lower freight costs and faster deliveries.

### Recommended Action
Launch a 12-month seller acquisition campaign targeting northern and central-west states. Recruit 500 new sellers distributed across RR, RO, MA, AC, AM, TO, PI, BA, GO, MT, MS.

**Incentives for New Sellers:**
- Waive Olist's onboarding fee for the first 6 months (normally R$500)
- Provide free logistics training (how to package efficiently, choose carriers)
- Guarantee 90-day payment terms instead of standard 120 days (improves cash flow for small sellers)

**Target Seller Profiles:**
- Small manufacturers of regional products (e.g., handicrafts, local food specialties)
- Existing brick-and-mortar retailers looking to expand online
- Dropshipping operators with local supplier relationships

### Expected Business Impact

**Freight Cost Reduction (Indirect):**
- More local sellers means shorter average shipping distances
- Target: 30% of orders in northern states fulfilled by local sellers within 18 months
- This reduces avg freight burden from 50% to 35% even without carrier renegotiation

**Revenue Diversification:**
- Adding 500 sellers in underserved states shifts GMV distribution
- Target: Reduce SP's revenue share from 42% to 35% within 24 months
- Increases platform resilience to regional economic shocks

**Order Volume Growth:**
- Local sellers improve product selection and delivery speed in remote regions
- Attracts customers who previously avoided Olist due to freight/delivery concerns
- Conservative estimate: 20% order volume growth in target states within 18 months

### Implementation Approach

**Phase 1: Market Research & Targeting (Months 1-2)**
- Identify 10 priority states based on population, internet penetration, and current seller density
- Build seller persona profiles (product categories, business size, digital maturity)
- Partner with local business associations (SEBRAE chapters, regional chambers of commerce)

**Phase 2: Campaign Launch (Months 3-6)**
- Digital advertising on Facebook/Instagram targeted to small business owners in priority states
- Host 5 regional seller recruitment events (in-person workshops in state capitals)
- Create localized landing pages with testimonials from existing regional sellers

**Phase 3: Onboarding & Support (Months 3-12)**
- Assign dedicated onboarding specialists to new sellers
- Provide training on inventory management, product photography, and customer service
- Offer 1-on-1 logistics consulting (how to choose carriers, negotiate rates)

**Phase 4: Performance Monitoring (Ongoing)**
- Track new seller retention rate (target: >70% still active after 12 months)
- Monitor order volume from new sellers (target: 5 orders/seller/month by month 6)
- Measure impact on regional freight costs and delivery times

### Resource Requirements
- **Budget**: R$200,000 for 12 months
  - R$80,000: Digital advertising and regional events
  - R$60,000: Onboarding fee waivers (500 sellers × R$500 × 24% expected take rate)
  - R$60,000: Dedicated onboarding specialist salaries (2 FTEs)
- **Headcount**: 2 Seller Success Managers (new hires)
- **Sales & Marketing Team**: Campaign design, landing page creation, event logistics (existing team, 20% allocation)

### Success Metrics
- Recruit 500 new sellers in target states within 12 months
- 70% seller retention rate at 12 months (350 sellers still active)
- New sellers collectively generate R$500,000 in GMV within 18 months
- Northern states' share of total platform GMV increases from 5% to 10%

### Risks & Mitigation
- **Risk**: New sellers in remote states lack digital literacy and struggle with platform tools
  - **Mitigation**: Provide hands-on training, simplified onboarding flow, and dedicated support hotline
- **Risk**: Low take rate from recruitment campaigns (sellers don't see value in Olist)
  - **Mitigation**: Highlight success stories from existing regional sellers, emphasize access to national customer base
- **Risk**: New sellers generate low order volume and churn quickly
  - **Mitigation**: Implement seller performance coaching (monthly check-ins, product listing optimization, marketing tips)

---

## What Was NOT Recommended (And Why)

### Option Considered: Build Olist-Owned Warehouses in Northern States
**Why Not Recommended:**
- Capital-intensive (R$2M+ per warehouse for facility, inventory, staff)
- High operational complexity (Olist becomes a logistics provider, not a marketplace aggregator)
- Long payback period (5+ years to ROI)
- Better alternatives exist (regional carrier partnerships achieve similar outcomes at 10% of the cost)

### Option Considered: Subsidize Freight Costs Directly for Customers
**Why Not Recommended:**
- Treats symptom (high freight) without addressing root cause (seller concentration, carrier inefficiency)
- Unsustainable economics (Olist's margins cannot absorb 30% freight subsidies indefinitely)
- Creates perverse incentives (sellers have no reason to optimize logistics if Olist pays freight)

### Option Considered: Focus Growth on Product Categories with Better Satisfaction Scores
**Why Not Recommended:**
- H5 (category hypothesis) was dropped during analysis—product categories were not the primary driver of satisfaction gaps
- Delivery performance matters more than product type
- Category focus doesn't solve geographic concentration or freight issues

---

## Recommendation Prioritization Summary

| Recommendation | Priority | Expected Impact | Investment Required | Payback Period |
|---|---|---|---|---|
| **1. Regional Carrier Partnerships** | High | 15% order volume growth in northern states | R$50K | 6 months |
| **2. Dynamic Delivery Windows** | High | 3.8 avg review score, <3% late rate | R$0 (internal dev) | 3 months |
| **3. Seller Acquisition Campaign** | Medium | 500 new sellers, 10% GMV from northern states | R$200K | 18 months |

**Total investment for all three recommendations: R$250,000 over 12 months.**

---

## Implementation Roadmap

**Months 1-2:** Launch Recommendation 2 (Dynamic Delivery Windows) — requires only engineering time, no budget  
**Months 3-4:** Initiate Recommendation 1 (Regional Carrier Partnerships) — RFP and pilot program  
**Months 3-6:** Start Recommendation 3 (Seller Acquisition Campaign) — market research and campaign launch  
**Months 5-6:** Full rollout of Recommendation 1 (carrier partnerships to 100% of orders)  
**Months 7-12:** Scale Recommendation 3 (onboarding and supporting new sellers)  

**By Month 12:** All three initiatives fully operational and showing measurable impact.

---

## Conclusion

These recommendations directly address the three gaps identified in the analysis:
1. Freight cost burden → Regional carrier partnerships
2. Delivery performance collapse → Dynamic delivery windows
3. Geographic revenue concentration → Seller acquisition in underserved states

They are sequenced to deliver quick wins (dynamic delivery windows, low cost/high impact) while building long-term strategic advantages (seller diversification, carrier network). If executed successfully, Olist can reduce its dependence on São Paulo, improve customer satisfaction in underserved regions, and unlock the next phase of growth.
