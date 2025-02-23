# Sales Data Analysis - README

## Project Overview
This project focuses on analyzing a sales dataset to uncover key business insights. The dataset contained 185,687 rows and 6 columns:

- **Order ID**
- **Product**
- **Quantity Ordered**
- **Price Each**
- **Order Date**
- **Purchase Address**

The goal was to clean the data, perform analysis using SQL Server, and visualize insights using Power BI.

---

## Technologies Used
- **Python (Pandas, Jupyter Notebook)** - For data cleaning and preprocessing
- **SQL Server** - For querying and analysis
- **Power BI** - For data visualization

---

## Data Cleaning and Preprocessing
The raw dataset was cleaned using Pandas with the following steps:
1. **Loading the dataset**
2. **Handling duplicates**
3. **Handling missing values**
5. **Converting order dates to datetime format**

Example Code:
```python
import pandas as pd
df = pd.read_csv('sales_data.csv')
df = df.drop_duplicates()
df.columns = df.columns.str.lower().str.replace(' ', '_')
df = df.dropna()
df['order_date'] = pd.to_datetime(df['order_date'])
```

---

## Data Analysis (SQL Queries)
The cleaned dataset was analyzed in SQL Server with the following queries:

- **Total Sales Revenue:**
```sql
SELECT SUM(Revenue) AS TotalRevenue FROM salesdata1;
```
- **Best-Selling Products:**
```sql
SELECT Product, SUM(Quantity_Ordered) AS TotalQuantitySold FROM salesdata1 GROUP BY Product ORDER BY TotalQuantitySold DESC;
```
- **Top Selling Cities:**
```sql
SELECT City, SUM(Revenue) AS TotalRevenue FROM salesdata1 GROUP BY City ORDER BY TotalRevenue DESC;
```
- **Peak Sales Hours:**
```sql
SELECT DATEPART(HOUR, Order_Date) AS OrderHour, SUM(Revenue) AS TotalRevenue FROM salesdata1 GROUP BY DATEPART(HOUR, Order_Date) ORDER BY TotalRevenue DESC;
```

---

## Data Visualization in Power BI
Key insights were visualized using:
- **Total Sales Revenue & Quantity Ordered** (Card visuals)
- **Sales by Product** (Bar Chart)
- **Best-Selling Products** (Table Visual)
- **Monthly Sales Trend** (Line Chart)
- **Sales by City** (Bar Chart)
- **Slicers for Product, Sales Month, and City**

---

## Key Findings
- **Highest revenue-generating product:** MacBook Pro Laptop
- **Most sold product by quantity:** AAA Batteries (4-pack)
- **City with the highest revenue:** San Francisco
- **Peak sales hour:** 7 PM
- **Sales peaks in certain months indicate seasonal demand**

---

## Recommendations
- **Stock high-demand products in profitable locations**
- **Target peak sales hours for promotions**
- **Analyze seasonal trends to optimize inventory**
- **Enhance product bundling strategies**
- **Investigate sales decline trends from 2019 to 2020**

---

## Conclusion
This analysis provided valuable business insights, enabling data-driven decision-making. By leveraging these findings, businesses can optimize sales strategies, improve inventory planning, and enhance marketing efforts.

