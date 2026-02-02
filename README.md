# Sales Data Analysis for Amazon

## Project Overview
This project provides a comprehensive analysis of Amazon's sales performance using a dataset of over 9,000 transactions. The goal was to identify key drivers of profitability, understand customer purchasing behavior across segments, and analyze regional sales distributions.

The project utilizes **Power BI** for interactive data visualization and **SQL** for data extraction and transformation logic.

 ---
 
## Key Performance Indicators (KPIs)
Based on the dashboard analysis:
* **Total Sales:** $2.30M
* **Total Profit:** $286.40K
* **Total Quantity Sold:** 37,873 units
* **Average Shipping Time:** 4 Days
  
---

## Tools & Technologies
* **Data Visualization:** Power BI Desktop
* **Data Source:** Amazon Sales Dataset (CSV)
* **Data Querying:** SQL (PostgreSQL / MySQL)
* **Data Cleaning:** Power Query (M Language)
  
---

## Dataset Schema
The dataset contains the following attributes:
* **Order Details:** Order ID, Order Date, Ship Date, Ship Mode
* **Customer Info:** Customer ID, Customer Name, Segment
* **Geography:** Country, City, State, Postal Code, Region
* **Product Info:** Product ID, Category, Sub-Category, Product Name
* **Metrics:** Sales, Quantity, Discount, Profit
  
---

## SQL Queries for Analysis
The following SQL queries represent the logic used to generate the dashboard components:

### 1. High-Level Summary (KPIs)
```sql
SELECT 
    SUM(Sales) AS Total_Sales,
    SUM(Profit) AS Total_Profit,
    SUM(Quantity) AS Total_Quantity,
    AVG(DATEDIFF(day, Order_Date, Ship_Date)) AS Avg_Shipping_Days
FROM amazon_sales;
```

### 2. Profitability by Category
```sql
SELECT 
    Category, 
    SUM(Profit) AS Total_Profit
FROM amazon_sales
GROUP BY Category
ORDER BY Total_Profit DESC;
```

### 3. Sales Distribution by Ship Mode
```sql
SELECT 
    Ship_Mode, 
    SUM(Sales) AS Total_Sales
FROM amazon_sales
GROUP BY Ship_Mode
ORDER BY Total_Sales DESC;
```

### 4. Regional Performance (Total Sales)
```sql
SELECT 
    Region, 
    SUM(Sales) AS Total_Sales
FROM amazon_sales
GROUP BY Region
ORDER BY Total_Sales DESC;
```

### 5. Monthly Profit Trends
```sql
SELECT 
    DATE_TRUNC('month', Order_Date) AS Month,
    SUM(Profit) AS Monthly_Profit
FROM amazon_sales
GROUP BY Month
ORDER BY Month;
```
---

## Dashboard Insights
Top Category: Technology is the most profitable category, followed by Office Supplies. Furniture has the lowest profit margin despite decent sales.

Regional Leader: The West region leads in total sales, while the South region represents the smallest market share.

Customer Segments: The Consumer segment is the largest contributor to both sales and profit (~47% of total profit).

Shipping: Standard Class is the most preferred shipping mode by customers.

---

## Conclusion
The analysis highlights that focusing on the 'Technology' category and the 'Consumer' segment in the 'West' region offers the highest growth potential.

---
