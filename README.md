
# 📊 Sales Performance Dashboard (Power BI)

## 📌 Project Overview
This project showcases an **interactive Sales Performance Dashboard** built using **Power BI**. It provides actionable insights into sales trends, profitability, customer behavior, and regional performance to support data-driven decision-making.

---

## 🎯 Objectives
- Build a **Star Schema data model**
- Create **DAX measures for KPIs**
- Implement **time intelligence (MoM growth)**
- Design an **executive-level dashboard**
- Generate **business insights and recommendations**

---

## 🧱 Data Modeling
- **Fact Table**: Orders  
- **Dimension Tables**: Customers, Products, Calendar  

### 🔗 Relationships
- Orders → Customers (Customer ID)  
- Orders → Products (Product ID)  
- Orders → Calendar (Order Date)  

---

## 📐 DAX Measures

### 🔹 Core KPIs
```DAX
Total Sales = SUM(Orders[Sales])

Total Profit = SUM(Orders[Profit])

Total Orders = DISTINCTCOUNT(Orders[Order ID])

Profit Margin = DIVIDE([Total Profit], [Total Sales])
````

### 🔹 Time Intelligence

```DAX
Previous Month Sales =
CALCULATE(
    [Total Sales],
    PREVIOUSMONTH(Calendar[Date])
)

Growth % =
VAR CurrentSales = [Total Sales]
VAR PrevSales =
    CALCULATE(
        [Total Sales],
        PREVIOUSMONTH(Calendar[Date])
    )
RETURN
IF(
    ISBLANK(PrevSales),
    BLANK(),
    DIVIDE(CurrentSales - PrevSales, PrevSales)
)
```

### 🔹 Contribution Analysis

```DAX
Category Contribution % =
DIVIDE(
    [Total Sales],
    CALCULATE([Total Sales], ALL(Products[Category]))
)
```

---

## 📅 Calendar Table

```DAX
Calendar =
ADDCOLUMNS(
    CALENDAR(
        MIN(Orders[Order Date]),
        MAX(Orders[Order Date])
    ),
    "Year", YEAR([Date]),
    "Month", FORMAT([Date], "MMM"),
    "Month Number", MONTH([Date]),
    "Year-Month", FORMAT([Date], "YYYY-MM")
)
```

---

## 📊 Dashboard Features

### 🔝 KPI Cards

* Total Sales
* Total Profit
* Total Orders
* Growth %
* Profit Margin

---

### 📈 Visualizations

* Line Chart → Monthly Sales Trend
* Column Chart → Sales by Region
* Bar Chart → Profit by Category
* Donut Chart → Sales by Segment
* Table → Top Customers

---

### 🎛️ Filters (Slicers)

* Year
* Year-Month
* Region
* Category
* Segment

---

## 📷 Dashboard Preview

<img width="1344" height="757" alt="Screenshot 2026-03-26 215916" src="https://github.com/user-attachments/assets/ae762553-2265-498a-958d-555a4ac8d49c" />


---

## 🔍 Key Insights

* Sales show **fluctuating trends over time**
* Some periods experience **negative growth**
* Profitability varies across **product categories**
* Sales are concentrated in **specific regions**
* A small number of customers contribute significantly to revenue

---

## 💡 Business Recommendations

* Optimize pricing and costs in **low-profit categories**
* Improve **growth consistency** using targeted campaigns
* Expand into **underperforming regions**
* Diversify customer base to reduce dependency on top clients
* Validate data anomalies (e.g., unusually high profit margin)

---

## 🛠️ Tools & Technologies

* Power BI
* DAX (Data Analysis Expressions)
* Data Modeling (Star Schema)

---

## 🚀 How to Use

1. Open the `.pbix` file in Power BI Desktop
2. Interact with slicers to explore insights
3. Analyze trends, performance, and business metrics

---

## 👤 Author

**Charu**

---

## ⭐ Acknowledgment

This project is part of a **Data Analytics & Business Intelligence task**, focused on building real-world dashboards using Power BI and DAX.

```
```
