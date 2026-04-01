# Superstore Sales Analysis (SQL - BigQuery)

## Overview
This project explores a retail dataset using SQL to understand how sales, profit, discounts, and customer behavior interact.

Instead of focusing only on revenue, the analysis looks at what actually drives (or reduces) profitability.

---

## Key Questions
- Which products generate sales but result in losses?
- Do higher discounts really help the business?
- Are high sales always profitable?
- How do customers differ in purchasing behavior?
- Which cities perform best in each region?
- How does sales change over time?

---

## Key Findings

- Some products still generate **negative profit despite having sales**  
- Higher discounts are often followed by **lower profit margins**  
- High sales do not always mean high profit  
- Customer activity varies, with some customers purchasing more frequently  
- Top-performing cities differ across regions  
- Sales fluctuate over time, showing changing patterns month to month  

---

## What This Means
The data suggests that:
- Revenue alone is not enough to measure performance  
- Discount strategy needs to be controlled carefully  
- Business performance depends on multiple factors, not just sales volume  

---

## Technical Notes
- SQL used: BigQuery  
- Techniques: aggregation, CTE, window functions (RANK, LAG)  
- Dataset is already clean (no major preprocessing required)  

---

## Closing
This project reflects my approach to data analysis:
not just writing queries, but trying to understand what the data is actually saying about the business.
