# Business Problem

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

- **Price** — freight costs on top of the product price may make purchases economically
  unviable for customers in certain regions.
- **Place** — seller supply and customer demand may not align geographically, leaving
  parts of the country underserved.
- **Process** — delivery is the one touchpoint Olist does not fully control; if it
  underperforms, it would likely surface in customer satisfaction data.
- **People** — marketplace revenue often follows a power law, where a small group of
  sellers disproportionately drives platform GMV.

These four areas became the basis for the hypotheses tested in the next section.

---

**Next Steps**: I formed 4 [business-hypotheses](./2-hypothesis) based on Olist's operating model and the structural challenges facing marketplace aggregators in geographically diverse markets.
