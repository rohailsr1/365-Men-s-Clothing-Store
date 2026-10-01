# 📊 365 Men's Clothing Store - Sales & Financial Analytics (Phase II)

![Python](https://img.shields.io/badge/Language-Python-3776AB?style=flat&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Library-Pandas-150458?style=flat&logo=pandas&logoColor=white)
![Excel](https://img.shields.io/badge/Tool-Excel-217346?style=flat&logo=microsoft-excel&logoColor=white)
![Power BI](https://img.shields.io/badge/Tool-Power%20BI-F2C811?style=flat&logo=powerbi&logoColor=black)
![Project Phase](https://img.shields.io/badge/Phase-II%20Data%20Cleaning%20%26%20EDA-blue)

---

## 📌 Project Overview

This project analyzes the multi-year sales performance, operational efficiency, and financial health of **365 Men's Clothing Store** from **2019 through 2022**. Building upon Phase I data ingestion, **Phase II** executes an end-to-end data cleaning pipeline, handles join losses, performs custom feature engineering (gross margins, discount values, date features), and delivers 5 key analytical visualizations.

---

## 📷 Dashboard & Visualizations Preview

The analysis is structured sequentially across 5 visual steps as defined in the project framework:

### 1️⃣ Visual 1: Multi-Year Revenue & Net Profit Trend (2019–2022)
![Yearly Revenue & Net Profit Trend](Images/Visual1_Yearly_Trends.png)
*Tracks annual performance trajectory, highlighting revenue stability across 2019–2022 and identifying annual margin peaks.*

### 2️⃣ Visual 2: Category & Product Performance Breakdown
![Product Performance Analysis](Images/Visual2_Product_Performance.png)
*Compares volume, total revenue, and profitability across T-Shirts, Hoodies, Sweaters, Jackets, and Socks.*

### 3️⃣ Visual 3: Geographic Revenue Distribution by City
![Geographic Revenue Distribution](Images/Visual3_Geographic_Distribution.png)
*Maps market contribution across primary regional hubs (Vancouver, Burnaby, Surrey) and secondary expansion markets.*

### 4️⃣ Visual 4: Shipping Logistics & Order Volume Analysis
![Shipping Logistics Analysis](Images/Visual4_Shipping_Logistics.png)
*Evaluates shipping fulfillment mix (Standard, Expedited, Nextday) and its revenue impact.*

### 5️⃣ Visual 5: Pricing, Discounting & Profitability Dynamics
![Pricing & Margin Dynamics](Images/Visual5_Margin_Dynamics.png)
*Analyzes effective discount impact on unit net profit and evaluates gross margin performance.*

---

## 🎯 Objectives

* **Audit & Clean Raw Data:** Reconcile data join anomalies (including the Coquitlam dataset loss) and remove duplicate transaction lines.
* **Engineer Financial & Temporal Features:** Compute `Gross_Margin`, `Revenue_Per_Unit`, `Discount_Value`, `Is_Weekend`, and `Year_Month`.
* **Evaluate Product Performance:** Identify high-volume baseline drivers versus high-margin premium categories.
* **Analyze Regional & Logistics Impact:** Determine key city revenue hubs and assess shipping method utilization.
* **Provide Actionable Retail Recommendations:** Deliver data-backed strategies to optimize store inventory, pricing, and shipping operations.

---

## 📂 Dataset Description & Data Quality Audit

The dataset records retail transactions from 2019 to 2022 covering store locations, product specifications, shipping details, and transaction pricing.

* 📊 **Dataset Size:** 603 order line items
* 📅 **Timeframe:** January 2, 2019 – December 29, 2022
* 🏬 **Retail Reach:** 12 Regional & International Store Locations

### 🔍 Data Quality Audit Findings (Phase II)
* **Join Data Loss Identified:** 51 shipping records (~7.8%) and 51 transaction lines (~7.72%) were lost during relational joins, all isolated to the **Coquitlam** city dataset.
* **Duplicate Removal:** Identified and eliminated 7 exact duplicate order rows (1.06% of initial rows).
* **Missing Value Imputation:** 4 missing shipping method fields (1.26%) were imputed with the standard operational mode (`Expedited`).

---

## 🛠️ Tools & Technologies

* **Python (Pandas, NumPy):** Data cleaning, missing value handling, feature engineering, and temporal aggregation.
* **Jupyter Notebook:** Executable analytics pipeline (`365Mens'sClothingPhaseII_Muhammad_Rohail.ipynb`).
* **Microsoft Excel:** Data preprocessing and tabular schema verification (`orders_data.xlsx`).
* **Power BI / Matplotlib / Seaborn:** Visual analytics and interactive dashboard rendering.

---

## 📊 Key Insights & Findings

### 💰 Financial & Revenue Performance
* **Total Revenue Generated:** **$45,682** with an aggregate **Net Profit of $32,509** (Overall Profit Margin: **~71.2%**).
* **Revenue Drivers:** **T-Shirts** lead overall sales volume (**821 units**, **$13,745** revenue), followed closely by **Hoodies** (**$11,040** revenue) and **Jackets** (**$9,740** revenue).
* **Profit Margins:** T-Shirts maintain exceptional profitability due to low cost-of-goods-sold ($2 avg. cost vs. $20 price), yielding **$12,103 in net profit**.

### 🌍 Geographic Insights
* **Top 3 Revenue Cities:** 
  1. **Vancouver:** $12,105 revenue (165 orders)
  2. **Burnaby:** $11,208 revenue (139 orders)
  3. **Surrey:** $9,606 revenue (130 orders)
* Metro Vancouver locations represent **~72% of total store revenue**, showing strong core market concentration.

### 🚚 Logistics & Shipping Operations
* **Standard Shipping** accounts for the vast majority of orders (**494 orders**, **$37,474 revenue**).
* **Expedited** (**59 orders**) and **Nextday** (**50 orders**) fulfill high-urgency demand, generating a combined **$8,208**.

---

## 📉 Key KPIs (Dashboard Summary)

| Metric | Value | Description |
| :--- | :--- | :--- |
| **Total Revenue** | **$45,682** | Cumulative gross sales across 4 years |
| **Total Net Profit** | **$32,509** | Net earnings after COGS and discounts |
| **Total Units Sold** | **1,807 units** | Total apparel garments sold |
| **Total Orders** | **603 orders** | Distinct order line items |
| **Average Unit Price** | **$25.58** | Mean catalog price |
| **Top Product Category** | **T-Shirt** | $13,745 Revenue (30.1% share) |
| **Top Performing Store/City** | **Vancouver** | $12,105 Revenue (26.5% share) |

---

## 📌 Conclusions

1. **Robust Core Profitability:** The product line enjoys high average gross margins (~71%), buffered by high-margin staple items like T-Shirts and Sweaters.
2. **Regional Concentration:** Sales are heavily concentrated in the Greater Vancouver area (Vancouver, Burnaby, Surrey), while international stores (Seoul, Tokyo, NY) remain early-stage.
3. **Consistent Multi-Year Sales:** Annual revenue remained steady between $9.8K and $12.3K per year, showing resilient baseline demand throughout 2019–2022.
4. **Clean Data Pipeline:** Phase II resolved duplicate records and cataloged join losses to ensure financial integrity for strategic decision-making.

---

## 🚀 Recommendations

* **Address Coquitlam Data Pipeline:** Investigate the data join architecture to recover missing shipping logs for Coquitlam transactions.
* **Capitalize on High-Margin Apparel:** Expand color variants and bundles for T-Shirts and Hoodies to drive higher basket sizes.
* **Target Regional Expansion:** Develop targeted marketing in secondary growth markets like Langley and Kelowna to replicate Vancouver's success.
* **Optimize Shipping Options:** Evaluate customer incentive programs (e.g., free Standard shipping thresholds) to convert high-value buyers.

---

## 👨‍💻 Author

**Muhammad Rohail**  
*Aspiring Data Analyst | Business Intelligence & Analytics*  
* **GitHub:** [Muhammad Rohail](https://github.com/)  
* **LinkedIn:** [Muhammad Rohail](https://linkedin.com/)