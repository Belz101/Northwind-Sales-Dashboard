##**Northwind Power BI Project – Full Documentation**
1. **Project Overview**

This project analyses the Northwind Traders dataset using Power BI to uncover insights into sales performance, product trends, customer behaviour, and order distribution. The goal is to create a recruiter-ready dashboard that demonstrates skills in data cleaning, modeling, DAX, and business intelligence storytelling.

The dashboard provides KPIs, monthly trends, top customers, category performance, and country-level insights to support data-driven decisions.
---
2. **Business Questions Answered**
- What is the total revenue generated?
- How many total orders were placed?
- Who are the top customers by revenue?
- Which product categories are the best-performing?
- What are the sales patterns across months and years?
- What is the average order value?
- How much quantity is sold overall?
- How do sales differ by country?
---
3. **Tools & Technologies Used**
- Power BI Desktop (data modelling, DAX, visualisations)
- Power Query (data cleaning & transformations)
- SQL (optional schema recreation & validation)
- DAX (measures & calculations)
- GitHub (version control & portfolio hosting)
---
4. **Dataset Description**

The following tables from the Northwind dataset were used:

|**Table**	  |**Description**                                                            |
-------------- ----------------------------------------------------------------------------
| Orders	    |Order-level info including order dates, customer, employee, shipper        |
| Order       |Details	Line-level detail including product, unit price, quantity         |
| Customers	  |Customer demographics (company, contact, city, country)                    |
| Products	  |Product information, including category                                    |
| Categories  |	Product category labels                                                   |
| Employees	  |Employee info (for linking orders)                                         |
| Shippers	  |Shipping company info                                                      |
| Calendar	  |Custom date table created in Power BI                                      |
---
5. **Data Cleaning & Transformation Steps**
**Power Query**
- Ensured correct data types (dates, text, integers, currency).
- Removed blank rows, duplicate entries, and invalid keys.
- Normalised column names (e.g., orderID → OrderID).
- Checked for missing CustomerID/ProductID values.
- Ensured date fields were converted to the Power BI Date type.

**Calendar Table**

Created using DAX to support time intelligence mechanisms:
- Date
- Year
- Month
- MonthName
- Quarter
- Year-Month

**(Optional) SQL**
- Created schema and imported CSVs
- Cleaned values using SQL queries
- Created validation queries to cross-check with Power BI totals
---
6. **Data Model (Star Schema)**

The data model follows a clean star schema centred on Order Details.

Relationships:

- Orders[OrderID] → Order Details[OrderID]
- Products[ProductID] → Order Details[ProductID]
- Categories[CategoryID] → Products[CategoryID]
- Customers[CustomerID] → Orders[CustomerID]
- Employees[EmployeeID] → Orders[EmployeeID]
- Shippers[ShipperID] → Orders[ShipVia]
- Calendar[Date] → Orders[OrderDate]

Schema Type:

Star Schema — fact table (Order Details) with surrounding dimension tables.
---
7. **DAX Measures Used**
-- Total Revenue
Total Revenue = SUMX('Order Details', 'Order Details'[UnitPrice] * 'Order Details'[Quantity])

-- Total Orders
Total Orders = DISTINCTCOUNT(Orders[OrderID])

-- Total Customers
Total Customers = DISTINCTCOUNT(Customers[CustomerID])

-- Total Quantity Sold
Total Quantity Sold = SUM('Order Details'[Quantity])

-- Average Order Value
Average Order Value = [Total Revenue] / [Total Orders]

-- Revenue by Month
Revenue by Month = 
CALCULATE(
    [Total Revenue],
    ALLEXCEPT(Calendar, Calendar[Year], Calendar[Month])
)

-- Top Customer Revenue
Top Customer Revenue = 
CALCULATE(
    [Total Revenue],
    TOPN(1, Customers, [Total Revenue], DESC)
)
---
8. **Visualisations Included**
- KPIs
- Charts
- Slicers
---
9. **Conclusion**
The dashboard provides a concise and clear analytical view into Northwind’s operations. It effectively demonstrates Power BI competencies, including modelling, transformations, DAX calculations, visual analytics, and insights communication. This project is structured for professional presentation to recruiters and hiring managers.
---

