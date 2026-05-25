# Data Dictionary

## Purpose

This document defines all calculated columns and custom fields created during the analysis. It serves as technical reference for anyone reviewing the Excel workbook or Tableau dashboard to understand how derived metrics were calculated and why they were needed.

---

## Part 1: Excel Calculated Columns (MASTER Sheet)

These columns were added to the MASTER sheet during the data transformation phase to enable pivot table analysis and hypothesis testing.

### 1. delivery_delay_days

**Data Type:** Integer  
**Formula:**
```excel
=DAYS(INT([@order_delivered_customer_date]),INT([@order_estimated_delivery_date]))
```

**Business Logic:**  
Calculates the number of days between the actual delivery date and the estimated delivery date. The `INT()` function strips the time component to focus on calendar days only.

**Interpretation:**
- Positive value = Late delivery (arrived AFTER estimated date)
- Zero = On-time delivery (arrived exactly on estimated date)
- Negative value = Early delivery (arrived BEFORE estimated date)

**Example:**  
Estimated: Jan 10, Actual: Jan 15 → `delivery_delay_days = +5` (5 days late)

**Used For:** H1 testing (delivery timing vs. review scores)

---

### 2. delivery_status

**Data Type:** Text (Categorical)  
**Formula:**
```excel
=IF([@delivery_delay_days]<0,"Early",IF([@delivery_delay_days]=0,"On Time","Late"))
```

**Business Logic:**  
Converts the numeric `delivery_delay_days` into a human-readable categorical status for easier pivot table grouping.

**Possible Values:**
- "Early" — Delivered before estimated date
- "On Time" — Delivered exactly on estimated date
- "Late" — Delivered after estimated date

**Used For:** Pivot Table 1 (Delivery Status vs. Avg Review Score)

---

### 3. delay_band

**Data Type:** Text (Ordinal)  
**Formula:**
```excel
=IF([@delivery_delay_days]<0,"Early",IF([@delivery_delay_days]=0,"On Time",IF([@delivery_delay_days]<=3,"Late 1-3 days",IF([@delivery_delay_days]<=7,"Late 4-7 days","Late 7+ days"))))
```

**Business Logic:**  
Segments late deliveries by severity to test whether review scores degrade progressively as delays worsen.

**Possible Values (Ordered):**
1. "Early"
2. "On Time"
3. "Late 1-3 days"
4. "Late 4-7 days"
5. "Late 7+ days"

**Example:**  
- Order delayed by 2 days → "Late 1-3 days"
- Order delayed by 10 days → "Late 7+ days"

**Used For:** Pivot Table 2 (Delay Severity vs. Avg Review Score), Tableau delay severity chart

---

### 4. order_purchase_month_year

**Data Type:** Text (Date formatted as "mmm yyyy")  
**Formula:**
```excel
=TEXT([@order_purchase_timestamp],"mmm yyyy")
```

**Business Logic:**  
Converts the full timestamp (e.g., "2017-08-15 14:23:11") into a month-year label (e.g., "Aug 2017") for time-series analysis.

**Example:**  
Input: `2017-11-22 09:15:33`  
Output: `"Nov 2017"`

**Used For:** Pivot Table 4 (Monthly Order Volume Trend), Tableau monthly growth chart

---

### 5. freight_pct

**Data Type:** Decimal (Percentage)  
**Formula:**
```excel
=([@freight_value]/[@price])*100
```

**Business Logic:**  
Calculates freight cost as a percentage of the product price to quantify the freight burden customers face relative to their order value.

**Example:**  
- Product price: R$100
- Freight cost: R$50
- `freight_pct = 50%`

**Interpretation:**  
Higher percentages indicate customers are paying disproportionately for shipping. Values above 50% mean freight costs more than half the product's value.

**Used For:** H4 testing (freight burden by state), Pivot Table 6, Tableau freight % by state chart

---

### 6. seller_state

**Data Type:** Text (State abbreviation)  
**Source:** Brought from RAW_sellers via XLOOKUP  
**Formula:**
```excel
=XLOOKUP([@seller_id],RAW_sellers[seller_id],RAW_sellers[seller_state])
```

**Business Logic:**  
Identifies where the product ships FROM (seller location). Essential for understanding delivery distance and seller geographic distribution.

**Example Values:** "SP", "MG", "RJ", "PR"

**Used For:** Seller concentration analysis, geographic maps showing seller vs. customer distribution

---

### 7. customer_state

**Data Type:** Text (State abbreviation)  
**Source:** Brought from RAW_customers via XLOOKUP  
**Formula:**
```excel
=XLOOKUP([@customer_id],RAW_customers[customer_id],RAW_customers[customer_state])
```

**Business Logic:**  
Identifies where the product ships TO (customer location). Used for revenue distribution analysis and freight burden calculations.

**Example Values:** "SP", "RJ", "MG", "RR", "RO"

**Used For:** H2 testing (revenue concentration), H4 testing (freight by state), geographic maps

---

### 8. product_category_name_english

**Data Type:** Text  
**Source:** Brought from RAW_translation via RAW_products  
**Formula (Two-step XLOOKUP):**

Step 1: Get Portuguese category name from RAW_products:
```excel
=XLOOKUP([@product_id],RAW_products[product_id],RAW_products[product_category_name])
```

Step 2: Translate to English:
```excel
=XLOOKUP([@product_category_name],RAW_translation[product_category_name],RAW_translation[product_category_name_english])
```

**Business Logic:**  
Original category names were in Portuguese. English translations make data readable for stakeholders unfamiliar with Portuguese.

**Example:**  
Portuguese: "beleza_saude"  
English: "health_beauty"

**Used For:** Category-level analysis (not emphasized in final recommendations but available for future deep dives)

---

## Part 2: Tableau Calculated Fields (GMV Pareto Dashboard)

These custom fields were created in Tableau to build the GMV Concentration Pareto Curve (Lorenz Curve) and dynamic KPI card. They deduplicate data at the order-item-seller grain and compute concentration ratios using Level of Detail (LOD) expressions and table calculations.

### 1. True GMV

**Data Type:** Measure (LOD Calculation)  
**Formula:**
```tableau
{FIXED [Order Id], [Product Id], [Seller Id] : MAX([Price])}
```

**Technical Function:**  
Deduplicates many-to-many order-payment relationships. The raw dataset has multiple payment records per order (e.g., customer pays with 2 credit cards). Summing `price` directly would overcount revenue. This LOD calculation ensures each order-product-seller combination contributes exactly one price value.

**Used For:** All Pareto curve and seller concentration calculations

---

### 2. % of Sellers

**Data Type:** Table Calculation  
**Formula:**
```tableau
INDEX() / SIZE()
```

**Technical Function:**  
Computes a continuous ranked percentage from 0% to 100% along the sorted seller list. `INDEX()` returns the current mark's position (1, 2, 3...), `SIZE()` returns total number of marks. Dividing gives the cumulative percentage.

**Example:**  
- Seller #592 out of 2,960 sellers → `INDEX() = 592`, `SIZE() = 2960` → `% of Sellers = 20%`

**Configuration:** Compute Using `Seller Id`, sorted descending by `True GMV`

**Used For:** X-axis of Pareto curve

---

### 3. Top 20% of Sellers

**Data Type:** Table Calculation (Boolean)  
**Formula:**
```tableau
[% of Sellers] <= 0.20
```

**Technical Function:**  
Evaluation gate that returns TRUE for sellers in the top 20% by GMV, FALSE for all others. Used to filter which sellers' revenue should be counted in the concentration ratio.

**Used For:** Filtering logic for `Top 20% Sellers GMV`

---

### 4. Top 20% Sellers GMV

**Data Type:** Table Calculation (Conditional Sum)  
**Formula:**
```tableau
IF [Top 20% of Sellers] THEN SUM([True GMV]) END
```

**Technical Function:**  
Isolates GMV earned by only the top 20% of sellers. If the seller is not in the top 20%, this returns NULL (excluded from aggregation).

**Used For:** Numerator in `Concentration Ratio` calculation

---

### 5. Concentration Ratio

**Data Type:** Nested Table Calculation  
**Formula:**
```tableau
WINDOW_SUM([Top 20% Sellers GMV]) / WINDOW_SUM(SUM([True GMV]))
```

**Technical Function:**  
Aggregates total GMV from the top 20% of sellers (numerator) and divides by total platform GMV (denominator). `WINDOW_SUM()` performs aggregation across the entire table partition.

**Result:** 0.8254 (82.54%)

**Configuration:** Compute Using `Seller Id`, sorted descending by `True GMV`

**Used For:** Y-axis reference line and KPI card dynamic text

---

### 6. Seller Count Rank

**Data Type:** Table Calculation  
**Formula:**
```tableau
INDEX()
```

**Technical Function:**  
Returns the running sequence number (1, 2, 3...) for each seller in the sorted partition. Used to label the annotation at the 20% mark.

**Example:**  
Seller ranked #592 → `Seller Count Rank = 592`

**Used For:** Dynamic annotation text showing exact number of sellers in top 20%

---

### 7. First Row Filter

**Data Type:** Table Calculation (Boolean)  
**Formula:**
```tableau
FIRST() == 0
```

**Technical Function:**  
Returns TRUE only for the first mark in the partition, FALSE for all others. Used on the KPI Card worksheet to display the concentration ratio exactly once (filters out 2,959 duplicate marks).

**Configuration:** Compute Using `Seller Id`

**Used For:** KPI Card filter (shows single headline text)

---

### 8. Dynamic Top 20% Count

**Data Type:** Measure (LOD Calculation)  
**Formula:**
```tableau
{ FIXED : COUNTD([Seller Id]) } * 0.20
```

**Technical Function:**  
Calculates 20% of the total unique seller count at the database level (not partition level). This ensures the KPI card always shows the correct number of sellers even if filters change.

**Result:** 2,960 × 0.20 = 592

**Number Format:** Custom, 0 decimal places

**Used For:** KPI Card dynamic text ("592 sellers")

---

## Data Sources

**Primary Dataset:** Olist Brazilian E-Commerce Public Dataset  
**Source URL:** https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce/data  
**Time Period:** September 2016 – August 2018  
**Total Orders:** 99,441 (96,478 delivered orders used for analysis)  
**Total Sellers:** 2,960  
**Total Customers:** 99,441  

**Files Used:**
1. olist_orders_dataset.csv
2. olist_order_items_dataset.csv
3. olist_customers_dataset.csv
4. olist_sellers_dataset.csv
5. olist_products_dataset.csv
6. olist_order_reviews_dataset.csv
7. olist_order_payments_dataset.csv
8. olist_geolocation_dataset.csv
9. product_category_name_translation.csv

---

## Data Quality Notes

- **Null Values:** No null values found in critical fields (order_id, customer_state, seller_state, price, freight_value, review_score) within the delivered orders subset
- **Duplicates:** Some orders had multiple payment records (many-to-many relationship). Handled via `True GMV` LOD calculation in Tableau.
- **Date Formats:** All timestamp fields were in ISO 8601 format (YYYY-MM-DD HH:MM:SS). Converted to date-only or month-year labels where needed.
- **State Abbreviations:** Brazilian state codes (2-letter) were used consistently across all location fields. No translation or cleaning required.

---

## Tool Versions

- **Excel:** Microsoft Excel for Mac (Version 16.XX) with Power Query enabled
- **Tableau:** Tableau Desktop 2023.3
- **Database Schema Tool:** draw.io (web version)
- **Process Mapping Tool:** draw.io (web version)
