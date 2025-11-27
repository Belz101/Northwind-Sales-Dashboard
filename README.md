# Northwind Sales Dashboard

## Project Overview
This project is a **single-page Power BI dashboard** analysing the Northwind dataset.  
It showcases **key sales KPIs, trends, product/category performance, and actionable insights** in a concise, recruiter-ready format.

**Objectives:**
- Visualise revenue and sales performance over time
- Highlight top-performing product categories and products
- Enable interactive filtering by Year, Month, and Product Category
- Summarise actionable insights for decision-making

Data Source: https://www.kaggle.com/datasets/jeetahirwar/northwind-traders

> Note: Only aggregated or anonymised data is included to respect privacy.

## Data Model & Relationships

**Relationships implemented in Power BI:**

| From Table      | Column        | To Table       | Column       | Relationship Type      |
|-----------------|---------------|----------------|-------------|----------------------|
| Orders          | CustomerID    | Customers      | CustomerID  | Many-to-One          |
| Orders          | EmployeeID    | Employees      | EmployeeID  | Many-to-One          |
| Orders          | ShipperID     | Shippers       | ShipperID   | Many-to-One          |
| Orders          | OrderID       | OrderDetails   | OrderID     | One-to-Many          |
| OrderDetails    | ProductID     | Products       | ProductID   | Many-to-One          |
| Products        | CategoryID    | Categories     | CategoryID  | Many-to-One          |

> All relationships are set to **single direction** for performance and accuracy in calculations.

---

**Core measures used in the dashboard:**

| Measure Name         | DAX Formula Example                                                          | Description                                  |
|--------------------- |------------------------------------------------------------------------------|----------------------------------------------|
| Total Revenue        | `SUMX('OrderDetails', 'OrderDetails'[Quantity] * 'OrderDetails'[UnitPrice])` | Total revenue from orders                    |
| Quantity Sold        | `SUM('OrderDetails'[Quantity])`                                              | Total products sold                          |
| YoY Revenue          | `CALCULATE([Total Revenue], SAMEPERIODLASTYEAR('Calendar'[Date]))`           | Year-over-Year revenue                       |
| MoM Revenue          | `CALCULATE([Total Revenue], DATEADD('Calendar'[Date], -1, MONTH))`           | Month-over-Month revenue                     |
| Order Month          | `FORMAT('Orders'[OrderDate], "MMM YYYY")`                                    | Helper column for trend analysis             |

## Dashboard Visuals

1. **KPI Cards:** Total Revenue, Quantity Sold, YoY Revenue, MoM Revenue  
2. **Slicers:** Year, Product Category, Month  
3. **Trend Line:** Total Revenue over time (with optional YoY overlay)  
4. **Category Chart:** Revenue by Product Category  
5. **Top N Chart:** Top 10 Products by Revenue  
6. **Insights Text Box:** Key takeaways and observations

## Key Insights

- **Top-performing category:** Beverages (35% of total revenue)  
- **Highest revenue month:** December, indicating strong holiday sales  
- **Top 3 products contributed 20% of total sales**  
- **Year-over-Year revenue growth:** 12%  

Screenshot of Canvas:
<img width="800" height="450" alt="image" src="https://github.com/user-attachments/assets/483bdea6-bd65-41dd-80eb-4b392948ef7a" />

---

## How to Use

1. Open `Northwind_Sales_Dashboard.pbix` in **Power BI Desktop**  
2. Use the **slicers** to filter by Year, Month, or Product Category  
3. Hover over visuals for detailed **tooltips**  
4. Explore trends, top categories/products, and summarised insights  

---

**Author:** Belaboh Gideon 
**Portfolio:** https://github.com/Belz101


