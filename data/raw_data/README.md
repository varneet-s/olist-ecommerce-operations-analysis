# Raw Data

## Data Source

The raw data for this analysis is publicly available on Kaggle:

**Dataset:** Olist Brazilian E-Commerce Public Dataset  
**URL:** https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce/data  
**Time Period:** September 2016 – August 2018  
**Total Records:** 99,441 orders across 9 CSV files

---

## Files Used

The following CSV files from Kaggle were imported into the Excel workbook `Olist_Business_Analysis.xlsx`:

1. **olist_orders_dataset.csv** — Order-level data (order_id, customer_id, order_status, timestamps)
2. **olist_order_items_dataset.csv** — Order line items (order_id, product_id, seller_id, price, freight_value)
3. **olist_customers_dataset.csv** — Customer information (customer_id, customer_state, customer_city)
4. **olist_sellers_dataset.csv** — Seller information (seller_id, seller_state, seller_city)
5. **olist_products_dataset.csv** — Product catalog (product_id, product_category_name, dimensions)
6. **olist_order_reviews_dataset.csv** — Customer reviews (order_id, review_score, review_comment)
7. **olist_order_payments_dataset.csv** — Payment information (order_id, payment_type, payment_value)
8. **olist_geolocation_dataset.csv** — Geographic coordinates (zip_code_prefix, lat, lng)
9. **product_category_name_translation.csv** — Portuguese to English category translations

---

## Data Access

To access the raw data:

1. Visit the Kaggle dataset page: https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce/data
2. Click "Download" to get all 9 CSV files
3. No Kaggle account required for download (public dataset)

---

## Analysis Workbook

The consolidated analysis workbook `Olist_Business_Analysis.xlsx` contains:
- All 9 raw CSV files as separate worksheets
- MASTER sheet with consolidated data and calculated columns
- DELIVERED_ONLY sheet (96,478 delivered orders used for analysis)
- 6 pivot tables testing hypotheses H1-H4

The workbook is available in this repository or upon request.

---

## Data License

The Olist dataset is released under the Creative Commons Attribution 4.0 International License (CC BY 4.0).

**Attribution:**
Olist Store. (2018). Brazilian E-Commerce Public Dataset by Olist. Retrieved from https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce/data
