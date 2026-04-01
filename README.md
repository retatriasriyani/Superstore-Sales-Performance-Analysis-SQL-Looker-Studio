# Superstore Sales Analysis (SQL - BigQuery)

## Overview
This project analyzes a retail dataset (Superstore) using SQL in BigQuery.  
The analysis focuses on understanding sales, profit, discount behavior, customer patterns, and regional performance.

---

## Objectives
- Identify products with negative profit  
- Compare performance across categories and subcategories  
- Analyze the impact of discount on profit  
- Understand customer purchasing patterns  
- Evaluate regional performance  
- Observe sales trends over time  

---

## Dataset Overview
The dataset contains transaction-level data, including:

- order_id  
- order_date (DATE format)  
- customer  
- product_name  
- category and subcategory  
- region and city  
- sales  
- profit  
- discount  

Notes:
- `order_date` is already in DATE format, so no parsing is required  
- `discount` is stored as numeric, so no cleaning is needed  

---

## Analysis

### 1. Product Profitability
This analysis identifies products with total profit below zero.

Finding:
Some products still generate sales but result in negative profit.

---

### 2. Category & Subcategory Performance
This section compares total sales and profit across categories and subcategories.

Finding:
There are differences between sales and profit across product groups.  
Some subcategories have relatively high sales but lower profit.

---

### 3. Discount Impact
Transactions are grouped based on discount level to compare performance.

Finding:
Higher discount levels tend to be associated with lower profit margins.

---

### 4. Customer Segmentation
Customers are grouped based on order frequency relative to the average.

Finding:
Customers show different purchasing frequencies, indicating variation in contribution.

---

### 5. Regional Performance
Cities are ranked within each region based on total profit.

Finding:
Top-performing cities differ across regions.

---

### 6. Sales Trend
Monthly sales are analyzed using order_date.

Finding:
Sales fluctuate over time, with both increases and decreases across months.

---

## Conclusion
The analysis shows that:
- Not all sales contribute positively to profit  
- Discount levels influence profitability  
- Customer behavior varies in frequency  
- Performance differs across regions and time  

This project demonstrates how SQL can be used to explore data and identify basic business patterns.
