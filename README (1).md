# 365 Men's Clothing Store — Retail Sales Analytics

End-to-end retail analytics case study using **Python, Pandas, NumPy, Matplotlib, Seaborn, Jupyter Notebook, and Excel** to evaluate sales performance, profitability, seasonality, product mix, geographic concentration, shipping behavior, and data quality for a men's clothing retailer.

The project covers transaction data from **2019–2022** and is structured as a two-phase analytical workflow: initial data preparation and an extended Phase II analysis with business-focused insights and visualizations.

---

## Project at a Glance

| Metric | Result |
|---|---:|
| Analysis period | 2019–2022 |
| Final transactions / orders | 603 |
| Units sold | 1,807 |
| Total revenue | **$45,682** |
| Total net profit | **$32,509** |
| Revenue from top 3 cities | **72.1%** |
| Peak month by combined revenue | **April — $5,319** |
| Lowest month by combined revenue | **June — $2,830** |

> **Note:** The notebook's `Gross_Margin` field is calculated as `Total Net Profit / Total Revenue × 100`. In this README, it is therefore described as a **net-profit-to-revenue margin** rather than a conventional accounting gross margin.

---

## Business Problem

The objective was to turn several raw retail datasets into a clean analytical dataset and answer practical business questions such as:

- How did revenue and net profit change from 2019 to 2022?
- Which product types generate the most revenue and profit?
- Which products have strong revenue but comparatively lower margins?
- Are sales concentrated in particular cities?
- What monthly patterns and weekday/weekend differences exist?
- How are customers using different shipping methods?
- How much discounting is taking place, and where?
- What data-quality issues could affect business conclusions?

The project emphasizes **business interpretation**, not just data cleaning and chart creation.

---

## Dataset

The project works with four source datasets:

- `Products.csv` — product name, price, cost, product type, and colour
- `Shipping.csv` — order ID, city, and shipping method
- `Stores.csv` — store ID and city mapping
- `Transactions.csv` — order ID, order line, product ID, date components, and quantity

`orders_data.xlsx` contains the integrated dataset used for the extended Phase II analysis.

The final analytical dataset covers **603 unique orders**, with no multi-line orders. Each recorded order therefore contains one purchased item, which is important when interpreting AOV, basket size, and cross-selling opportunities.

---

## Analytical Workflow

```text
Raw CSV files
     │
     ├── Products
     ├── Shipping
     ├── Stores
     └── Transactions
            │
            ▼
     Data quality checks
            │
            ├── Missing-value handling
            ├── Store ID completion
            ├── Duplicate detection
            └── Join reconciliation
            │
            ▼
      Integrated order data
            │
            ▼
      Feature engineering
            │
            ├── Total Revenue
            ├── Total Cost
            ├── Total Net Profit
            ├── Margin metric
            ├── Revenue per Unit
            ├── Discount Value
            ├── Day of Week
            ├── Weekend / Weekday flag
            └── Year-Month
            │
            ▼
       Business analysis
            │
            ├── Financial trends
            ├── Seasonality
            ├── Product analysis
            ├── Colour analysis
            ├── City analysis
            ├── Shipping analysis
            └── Data integrity
            │
            ▼
     Recommendations & limitations
```

---

## Data Quality & Cleaning

A major part of the project was validating whether the final dataset accurately represented the source files.

| Data-quality check | Finding | Treatment |
|---|---|---|
| Missing Store IDs | 10 missing values in `Stores.csv` | Populated using the store sequence used by the dataset |
| Missing shipping methods | 9 missing values in the raw shipping file | Filled with `Expedited` during preparation |
| Exact duplicate transactions | 7 rows | Removed; approximately **1.06%** of raw transaction rows |
| Shipping join loss | 51 records, **7.8%** of raw shipping records | Investigated and traced to **Coquitlam** |
| Transaction join loss | 51 records, **7.72%** of raw transaction lines | Investigated and traced to **Coquitlam** |

The join-loss investigation was especially important because those records were not random: the missing rows were concentrated in a single city. The project therefore flags **Coquitlam as an analytical coverage gap** rather than silently treating the integrated dataset as complete.

---

## Key Business Findings

### 1. Financial Performance: 2019–2022

| Year | Revenue | Revenue YoY | Net Profit | Net Profit YoY |
|---|---:|---:|---:|---:|
| 2019 | $12,297 | — | $8,535 | — |
| 2020 | $9,856 | -19.85% | $7,088 | -16.95% |
| 2021 | $12,179 | +23.57% | $8,622 | +21.64% |
| 2022 | $11,350 | -6.81% | $8,264 | -4.15% |

The analysis shows a clear contraction in 2020, a strong recovery in 2021, and a moderate decline in 2022. The highest annual revenue occurred in **2019**, while the highest annual net profit occurred in **2021**.

---

### 2. Product Mix & Profitability

| Product Type | Revenue | Net Profit | Net Profit / Revenue |
|---|---:|---:|---:|
| T-shirt | $13,745 | $12,103 | 88.05% |
| Hoodie | $11,040 | $6,495 | 58.83% |
| Jacket | $9,740 | $5,900 | 60.57% |
| Sweater | $9,365 | $6,415 | 68.50% |
| Socks | $1,792 | $1,596 | 89.06% |

The product analysis highlights a useful distinction between **revenue scale** and **margin performance**:

- **T-shirts** generate the highest revenue and the highest aggregate net profit among product types.
- **Hoodies** are the second-largest revenue contributor but have a much lower margin than T-shirts and Socks.
- **Socks** generate the lowest revenue but maintain a very high margin percentage.
- The revenue ranking and margin ranking do not match, showing why product decisions should consider both scale and profitability.

---

### 3. Geographic Revenue Concentration

| City | Revenue | Orders |
|---|---:|---:|
| Vancouver | $12,105 | 165 |
| Burnaby | $11,208 | 139 |
| Surrey | $9,606 | 130 |
| Langley | $5,592 | 73 |
| New York | $1,284 | 14 |
| Kelowna | $1,090 | 10 |
| Los Angeles | $1,069 | 16 |
| Portland | $1,021 | 15 |
| Seattle | $967 | 12 |
| Tokyo | $815 | 10 |
| San Diego | $681 | 13 |
| Seoul | $244 | 6 |

The **top three cities account for 72.1% of total revenue**, and the top four account for roughly 84%. This indicates substantial geographic concentration and creates a clear business question around the causes of lower sales in other locations.

The dataset alone cannot establish the root cause of those differences because customer-level information, inventory availability, and market-preference research are not included.

---

### 4. Seasonality

Across the combined 2019–2022 period:

- **April** was the highest-revenue month at **$5,319**.
- **June** was the lowest-revenue month at **$2,830**.
- December also showed relatively strong revenue at **$5,031**.

The pattern suggests meaningful monthly variation, but the analysis aggregates all four years together. It should therefore be treated as a **combined-period seasonal pattern**, not proof that the exact same monthly ranking occurred in every individual year.

---

### 5. Weekday vs Weekend Sales

| Day Type | Revenue | Orders | Revenue Share | Revenue per Calendar Day |
|---|---:|---:|---:|---:|
| Weekday | $29,518 | 401 | 64.62% | $5,903.60 |
| Weekend | $16,164 | 202 | 35.38% | $8,082.00 |

Weekdays generate more total revenue because there are five weekdays versus two weekend days. However, when normalized by the number of calendar days, **average daily weekend revenue is about 37% higher** than average weekday revenue.

This distinction is useful for staffing, store activity, and campaign timing because raw totals alone can hide the difference in the number of selling days.

---

### 6. Shipping Behaviour

| Shipping Method | Revenue | Orders | Average Order Value |
|---|---:|---:|---:|
| Standard | $37,474 | 494 | $75.86 |
| Expedited | $4,604 | 59 | $78.03 |
| Nextday | $3,604 | 50 | $72.08 |

**Standard shipping represents about 82% of orders and revenue**, making it the dominant fulfillment method.

Expedited orders have a slightly higher average order value than Standard orders, but this difference should be interpreted cautiously because some shipping values were imputed during data preparation.

---

### 7. Discounting

The analysis found a total calculated discount value of **$254.10** across the final dataset. Discounting was concentrated in **Socks**, where a 30% discount was applied to Green and Grey variants.

This is a useful pricing observation because the discount activity was highly concentrated rather than spread across the broader product range.

---

### 8. Colour Performance

Sales volume and revenue were concentrated in **White and Black**, while Red had the lowest recorded quantity and the lowest margin metric among the six colours analysed.

However, the dataset does not include enough information to determine whether low Red sales were caused by customer preference, product design, assortment, display, or availability. The notebook explicitly treats this as a **follow-up investigation rather than a definitive product decision**.

---

## Strategic Recommendations

### Expand the seasonal assortment

The dataset is heavily weighted toward winter-oriented product types such as Hoodies, Jackets, and Sweaters, while T-shirts are the main summer-oriented category. Expanding the summer assortment could reduce dependence on a narrow product mix during warmer months.

### Investigate geographic performance before expanding further

With 72.1% of revenue coming from the top three cities, future store expansion should be supported by local customer, market, and assortment research. Revenue alone cannot explain why some locations perform differently.

### Improve basket-building opportunities

All 603 recorded orders contain a single item. That means traditional market-basket analysis cannot be performed on this dataset, but it also highlights an opportunity to test bundling and accessory-led upselling in future transactions.

### Strengthen the data pipeline

The 51 shipping records and 51 transaction lines lost during joins should be investigated at the source-system level, particularly because all identified losses relate to Coquitlam. Recovering or reconciling these records would improve analytical coverage.

### Add inventory and customer data to the next analysis phase

Inventory data would enable sell-through, stock-to-sales, stock ageing, overstock/understock, and inter-store transfer analysis. Customer-level data would enable retention, customer AOV, lifetime value, and segmentation analysis.

---

## What the Dataset Cannot Answer

The available data is sufficient for sales, product, geographic, shipping, discount, and basic profitability analysis, but several important retail questions remain outside scope:

- Customer lifetime value and retention
- Customer-level average order value and segmentation
- Inventory shortages, overstock, ageing, and sell-through
- Stock-to-sales and inventory productivity ratios
- Inter-store stock transfer recommendations
- Marketing campaign ROI beyond the recorded discount activity
- Root-cause analysis for underperforming cities

These limitations are part of the analysis rather than something to hide; documenting them helps distinguish **what the data shows** from **what would require additional data**.

---

## Visual Analysis

The notebooks include visual analysis covering:

- Revenue and net profit by product type
- Revenue trends across 2019–2022
- Monthly revenue / seasonality
- Weekday vs weekend performance
- Revenue by city
- Revenue by shipping method and city
- Revenue by colour
- Product-type revenue across cities using a heatmap
- Margin comparisons by product type and colour

---

## Repository Structure

```text
365-Men-s-Clothing-Store/
│
├── 365Mens'sClothingPhaseII_Muhammad_Rohail.ipynb  # Main Phase II analysis
├── Python - Case Study.ipynb                       # Initial data preparation / case study
├── Products.csv                                    # Product master data
├── Shipping.csv                                    # Shipping data
├── Stores.csv                                      # Store master data
├── Transactions.csv                                # Transaction data
├── orders_data.xlsx                                # Integrated analysis dataset
├── Images/                                          # Project images
├── 365 Men's Clothing Store.png                    # Project logo
└── readme.md                                       # Project documentation
```

---

## How to Run

### 1. Clone the repository

```bash
git clone https://github.com/rohailsr1/365-Men-s-Clothing-Store.git
cd 365-Men-s-Clothing-Store
```

### 2. Install dependencies

```bash
pip install pandas numpy matplotlib seaborn openpyxl jupyter
```

### 3. Launch Jupyter Notebook

```bash
jupyter notebook
```

Open `365Mens'sClothingPhaseII_Muhammad_Rohail.ipynb` and run the notebook cells in order.

> The notebook expects the CSV files and `orders_data.xlsx` to be available in the working directory.

---

## Core Skills Demonstrated

**Python:** Pandas, NumPy, data cleaning, joins, grouping, aggregation, feature engineering

**Data Quality:** Missing-value handling, duplicate detection, join-loss reconciliation, key validation

**Analytics:** YoY analysis, profitability analysis, seasonality, geographic concentration, shipping analysis, pricing/discount analysis

**Visualization:** Matplotlib, Seaborn, business-focused charts and heatmaps

**Business Thinking:** Translating descriptive analysis into retail questions, recommendations, and data requirements for the next analytical phase

---

## Notebooks

- **[Phase II — Main Analysis](./365Mens'sClothingPhaseII_Muhammad_Rohail.ipynb)**
- **[Python Case Study — Data Preparation](./Python%20-%20Case%20Study.ipynb)**

---

## Author

**Muhammad Rohail**  
Data Analyst | Business Intelligence & Retail Analytics

[GitHub Profile](https://github.com/rohailsr1)

---

## Project Focus

This project was built to demonstrate an end-to-end **retail data analytics workflow**: starting with imperfect source data, validating and transforming it, analysing business performance, identifying limitations, and communicating findings in a way that supports practical decision-making.
