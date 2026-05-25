# Business Problem Diagnosis

## Organisation Background
Olist is a Brazilian e-commerce marketplace aggregator that connects small and medium-sized
sellers to major platforms like Mercado Livre, B2W, and Via Varejo. Sellers pay a single
fee to list across all platforms under one consolidated agreement — Olist manages marketplace
relationships while sellers fulfil orders directly.

The dataset covers approximately 99,000 orders placed between 2016–2018 across Brazil's
27 states.

---

## Problem Diagnosis

Before opening the dataset, I used the **6P framework** (Product, Price, Place, Promotion,
People, Process) as a structured lens to think through what problems a marketplace aggregator
operating at Brazil's geographic scale could plausibly face.

Applied across the 6Ps, four areas emerged as worth investigating:

- **Price** — freight costs on top of product price may make purchases economically
  unviable for customers in certain regions
- **Place** — seller supply and customer demand may not align geographically, leaving
  parts of the country underserved
- **Process** — delivery is the one touchpoint Olist does not fully control; if it
  underperforms, it would likely surface in customer satisfaction data
- **People** — marketplace revenue often follows a power law, where a small group of
  sellers disproportionately drives platform GMV

---

## Business Questions

These four questions guided the analysis. They are referenced throughout the project
as H1–H4 for consistency.

- **H1** — Could delivery delays be reducing customer satisfaction scores, and if so,
  by how much?
- **H2** — Which states drive the majority of Olist's revenue, and how concentrated
  is that?
- **H3** — What percentage of sellers are responsible for the majority of GMV?
- **H4** — Which states have disproportionately high freight costs relative to order
  value?

---

**Next Step**: I tested these questions through data analysis and visualisation in
[Analysis →](./4-analysis.md), but first mapped out the key stakeholders whose decisions
would be shaped by the findings in [Stakeholder Map →](./2-stakeholder-map.md)
