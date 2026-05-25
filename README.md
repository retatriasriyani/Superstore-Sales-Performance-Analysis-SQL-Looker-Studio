# Superstore Sales Analysis (SQL - BigQuery)

## Overview

This project analyzes a retail sales dataset using SQL in BigQuery to understand business performance, profitability trends, customer behavior, and sales patterns across a 4-year period (January 2019 – December 2022).

Rather than focusing only on revenue, the analysis explores the factors that influence profitability and overall business performance.

---

## Executive Summary

This project analyzes over 9,900 retail sales transactions using SQL in BigQuery to evaluate sales performance, profitability trends, customer purchasing behavior, and regional business performance.

Key findings reveal that high sales do not always lead to high profitability — products with aggressive discount strategies consistently generate negative profit margins. A small group of customers (top 10) contributes 15.6% of total revenue, and the Central region is the only region operating at a loss (-9% margin). Interactive dashboards were developed in Looker Studio to support data visualization and business decision-making.

> **Data Quality Note:** During exploratory analysis, approximately 4,825 rows (~48%) were identified with profit values inconsistent with their corresponding sales figures — likely due to a data entry or transformation error in the source dataset. These rows were excluded from profit-related analyses. All findings below are based on 5,169 validated rows. This filtering decision is documented in the SQL cleaning step.

---

## Business Problem

Retail businesses often focus heavily on increasing sales revenue without fully understanding the factors affecting profitability and long-term business performance.

High sales volume does not always generate strong profits, especially when discount strategies, product performance, and customer purchasing behaviors are not properly evaluated. Businesses also need to understand regional performance differences and changing sales trends to support better operational and strategic decisions.

This project aims to analyze retail sales data to identify profitability drivers, customer behavior patterns, and business performance trends using SQL-based analysis.

---

## Project Objectives

- Analyze overall sales and profit performance across 4 years of transaction data
- Identify products with high sales but low or negative profitability
- Evaluate the impact of discount strategies on profit margins
- Analyze customer purchasing behavior and segmentation
- Compare regional business performance
- Identify monthly sales trends and seasonal patterns
- Develop interactive dashboards for business monitoring

---

## Key Performance Indicators (KPIs)

> **Data Scope Note:** Metrics are split into two scopes. Columns unaffected by the profit anomaly — `sales`, `CustomerID`, `InvoiceDate`, `order_id`, `product_name` — use the **full dataset (9,993 rows)**. Any metric involving `profit` or `profit_margin` uses only **validated rows (5,169)** where profit values are mathematically consistent with their corresponding sales figures.

| Metric | Value | Data Scope |
|---|---|---|
| Total Transactions | 9,993 rows | ✅ Full dataset |
| Total Customers | 793 | ✅ Full dataset |
| Total Orders | 5,009 | ✅ Full dataset |
| Total Products | 1,850 | ✅ Full dataset |
| Analysis Period | Jan 2019 – Dec 2022 | ✅ Full dataset |
| Valid Transactions (profit analysis) | 5,169 rows | ⚠️ Validated rows only |
| Total Sales | ~$785M | ⚠️ Validated rows only |
| Overall Profit Margin | 10.4% | ⚠️ Validated rows only |

---

## Key Questions

- Which products generate high sales but result in losses?
- Do higher discounts improve or reduce profitability?
- Are high sales always associated with high profit?
- How do customer purchasing behaviors differ?
- Which regions perform best — and worst?
- How do sales trends change over time?

---

## Key Findings

### 1. Product Profitability
> ⚠️ *Based on validated rows only (5,169) — rows where profit is mathematically consistent with sales*

- **257 out of 1,529 products (16.8%)** generated negative profit despite positive sales
- The worst-performing product by margin: **O'Sullivan Living Dimensions 5-Shelf Bookcases** — $17.4M in sales but **-31.3% profit margin (-$5.4M loss)**
- The highest-loss product by absolute value: **O'Sullivan Plantations 2-Door Library** — $23.5M in sales but **-$5.6M profit loss (-23.9% margin)**
- Most profitable product: **Canon imageCLASS 2200 Advanced Copier** — 82% profit margin

### 2. Discount Impact
> ⚠️ *Based on validated rows only (5,169)*

| Discount Level | Profit Margin |
|---|---|
| No discount | **+36.8%** |
| Low discount (0–20%) | **+30.5%** |
| Medium discount (20–50%) | **-21.3%** |
| High discount (>50%) | **-84.9%** |

Transactions with discounts above 20% consistently produce **negative profit margins**, confirming that aggressive discounting significantly destroys profitability.

### 3. Customer Behavior
> ✅ *Based on full dataset (9,993 rows) — frequency and sales columns are unaffected by the profit anomaly*

- **54% of customers (419 out of 781)** are Low Value customers — purchasing below the average frequency of 6.6 orders
- **19% of customers (149)** are High Value — purchasing more than 1.5x the average frequency
- **Top 10 customers contribute 15.6% of total revenue**, with Anna Gayman leading at $24.8M in total purchases
- High-frequency customers (Emily Phan with 11 orders, Patrick O'Brill with 14 orders) are not always the highest spenders — indicating value and frequency are distinct retention levers

### 4. Regional Performance
> ⚠️ *Profit margin figures based on validated rows only (5,169). Sales figures use full dataset.*

| Region | Total Sales | Profit Margin |
|---|---|---|
| West | $284.3M | **+25.8%** ✅ |
| East | $153.4M | **+17.4%** ✅ |
| South | $94.8M | **+4.8%** ✅ |
| Central | $252.9M | **-9.0%** ❌ |

The Central region generates the second-highest sales volume but is the **only region operating at a loss**, suggesting structural pricing or cost issues that require targeted investigation.

### 5. Category & Sub-Category Performance
> ⚠️ *Based on validated rows only (5,169)*

**Worst subcategories by margin:**
- Furniture – Tables: **-38.4% margin** (-$33M loss)
- Office Supplies – Binders: **-8.0% margin**
- Furniture – Bookcases: **-8.0% margin**

**Best subcategories by margin:**
- Technology – Copiers: **+82.4% margin**
- Technology – Phones: **+63.1% margin**
- Office Supplies – Appliances: **+60.6% margin**

### 6. Customer Segment Performance
> ⚠️ *Profit margin figures based on validated rows only (5,169)*

| Segment | Profit Margin |
|---|---|
| Home Office | **14.3%** — most profitable |
| Corporate | 10.5% |
| Consumer | 9.2% — largest segment, lowest margin |

### 7. Sales Trend
> ✅ *Based on full dataset (9,993 rows) — sales and date columns are unaffected by the profit anomaly*

- Sales show clear **seasonal growth patterns**, peaking in **September 2021 ($56M)** — the highest single month across the 4-year period
- February consistently shows the lowest monthly sales (Feb 2019: $377K), suggesting a post-Q1 slowdown
- Year-over-year growth is visible from 2019 to 2022 with a strong Q4 acceleration each year

---

## Business Insights

- **Revenue alone is not a sufficient performance indicator.** The Central region ranks second in sales but is the only loss-making region.
- **Discount strategies above 20% are consistently harmful to profitability.** Medium and high discounts both produce negative margins.
- **A small group of customers drives disproportionate revenue.** Retaining the top 10% of high-value customers should be a strategic priority.
- **Furniture subcategories (Tables, Bookcases) are structurally unprofitable** and likely require a fundamental pricing review rather than incremental adjustments.
- **Technology products — especially Copiers and Phones — are the strongest profit drivers** and should be prioritized in sales and marketing investment.

---

## Business Recommendations

1. **Revise discount policy**: Cap discounts at 20% across all categories. Medium and high discounts (>20%) consistently produce negative margins and should require management approval.
2. **Focus retention on high-value customers**: The top 10 customers contribute 15.6% of revenue. A dedicated account management or loyalty program for this group would have high ROI.
3. **Review Furniture pricing structure**: Tables (-38% margin) and Bookcases (-8% margin) are structural loss-makers. Consider price adjustments, supplier renegotiation, or deprioritizing these lines.
4. **Investigate Central region operations**: Despite $252M in sales, the Central region generates a -9% margin. A deeper audit of regional pricing, discounting behavior, and cost structure is recommended.
5. **Prioritize Technology category in marketing**: Copiers (+82%) and Phones (+63%) generate the strongest margins and should receive higher marketing investment.
6. **Use seasonal trend data for inventory planning**: September–November consistently shows sales peaks. Stocking and promotional planning should align with this cycle.

---

## Technical Notes

### Tools
- SQL (BigQuery)
- Looker Studio
- Microsoft Excel

### SQL Techniques
- Aggregation (`SUM`, `COUNT`, `AVG`, `ROUND`)
- Common Table Expressions (CTE)
- Window Functions (`RANK()`, `LAG()`)
- `CASE WHEN` for conditional segmentation
- Data quality filtering using margin validation
- Trend Analysis with month-over-month growth calculation

### Dataset
- Superstore Dataset (Kaggle)
- 9,993 transactional records | Jan 2019 – Dec 2022
- 793 unique customers | 1,850 unique products
- Data cleaning applied: excluded ~4,825 rows with corrupted profit values (profit inconsistent with sales figures)

---

## Interactive Dashboard

[View Looker Studio Dashboard](https://datastudio.google.com/reporting/651229bb-3218-411c-9bb7-f4e3788a29d9)

---

## Conclusion

This project demonstrates how SQL can be used to analyze retail business performance beyond basic sales reporting — including data quality validation, profitability analysis, customer segmentation, regional comparison, and trend evaluation.

A key analytical decision in this project was identifying and handling corrupted profit data before drawing conclusions — demonstrating the importance of data validation as a foundational step before any business analysis.

The analysis shows that high revenue does not always lead to strong profitability, and factors such as discount strategies, product mix, and regional dynamics significantly influence overall business performance.
