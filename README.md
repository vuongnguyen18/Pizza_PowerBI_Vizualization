# Pizza Sales Analytics Dashboard

## Project Overview

This project presents an end-to-end **Pizza Sales Analytics Dashboard** built in **Power BI** to analyse restaurant sales performance, product demand, customer ordering behaviour, and operational efficiency. The dashboard is designed as a portfolio-style business intelligence project, focusing on turning raw transactional pizza sales data into clear, interactive insights for management decision-making.

The report contains five main dashboard pages:

1. **Executive Report** – high-level business performance summary.
2. **Monthly Report** – month-specific revenue, order, and product performance analysis.
3. **Time-Based Sales Insights** – sales patterns by month, weekday, day, and hour.
4. **Product Insights** – category, pizza size, and ingredient-level analysis.
5. **Operational Performance Analysis** – order structure, turnaround time, and price-volume relationship.

---

## Business Objectives

The main objective of this project is to answer the following business questions:

- Which pizza categories and individual pizzas generate the highest revenue and sales volume?
- How do sales and orders change across months, weekdays, weekends, and trading hours?
- Which pizza sizes and ingredients are most popular across different categories?
- Are customers more likely to place single-item or multi-item orders?
- Is there a relationship between average pizza price and quantity sold?
- What operational patterns can be observed from order turnaround time?

---

## Tools and Technologies

- **Power BI Desktop** – data modelling, DAX measures, dashboard design, and interactive reporting.
- **Power Query** – data cleaning, transformation, column formatting, and table preparation.
- **DAX** – KPI measures, ranking logic, dynamic metric selection, moving average calculations, and correlation analysis.
- **Data Modelling** – star schema design with fact and dimension tables.
- **GitHub** – project documentation and portfolio presentation.

---

## Data Preparation and Modelling

The original pizza sales dataset was transformed into a reporting-ready model in Power BI with careful attention to data granularity. The main sales fact table was kept at the original **order-line level**, where each row represents one pizza item within a customer order. This design ensures that core sales measures such as revenue, quantity sold, order count, and average order value are calculated accurately without duplication.

A key modelling issue addressed in this project was the treatment of pizza ingredients. Instead of expanding the main order detail table by ingredient, ingredients were separated into their own mapping structure. This was important because expanding each pizza line by ingredient would repeat the same sales transaction multiple times. As a result, measures such as total revenue and total quantity sold would be artificially inflated when ingredient-level analysis is performed.

To avoid this problem, the model separates sales transactions from ingredient relationships. The order detail table remains at the pizza order-line grain, while ingredients are split into rows in a separate bridge table. This approach is more scalable than splitting ingredients into fixed columns such as Ingredient 1, Ingredient 2, and so on. A fixed-column design assumes a maximum number of ingredients per pizza, which may not hold true if new pizzas are added in the future. By storing ingredients as rows, the model can support any number of ingredients without data loss or additional restructuring.

Key modelling decisions included:

- Kept the main `Fact_Order_Detail` table at the original order-line level.
- Created supporting dimension tables such as `Dim_Date`, `Dim_Pizza`, `Dim_Category`, `Dim_Size`, and `Dim_Ingredient`.
- Built a separate pizza-ingredient bridge table to handle the many-to-many relationship between pizzas and ingredients.
- Split comma-separated ingredient values into rows rather than fixed columns to improve scalability and flexibility.
- Avoided expanding the sales fact table by ingredients to prevent revenue and quantity inflation.
- Created DAX measures for core KPIs such as total revenue, total orders, total quantity sold, average order value, and average pizzas per order.
- Added ranking slicers for Top 5 / Bottom 5 analysis.
- Created dynamic metric selection for switching between Total Quantity Sold and Total Revenue.
- Added navigation buttons to improve report usability across dashboard pages.

---

## Key Performance Indicators

The report tracks the following core KPIs:

| KPI | Value |
|---|---:|
| Total Revenue | $817.6K |
| Total Orders | 21,350 |
| Total Quantity Sold | 49.57K |
| Average Order Value | $38.31 |
| Average Pizzas per Order | 2.32 |

---

## Dashboard Pages and Insights

### 1. Executive Report

The Executive Report provides a high-level overview of business performance. Total revenue reached **$817.6K** from **21,350 orders**, with **49.57K pizzas sold**. The average order value was **$38.31**, and customers purchased an average of **2.32 pizzas per order**.

Revenue was relatively balanced across categories, with **Classic** generating the highest revenue at approximately **$220K**, followed by **Supreme ($208K)**, **Chicken ($196K)**, and **Veggie ($194K)**. Monthly revenue fluctuated across the year, with **July** recording the highest monthly revenue at approximately **$72.6K**, while **September and October** were the lowest months at around **$64K**.

The top revenue-generating pizzas were led by **The Thai Chicken Pizza** and **The Barbecue Chicken Pizza**, both contributing approximately **$43K** in revenue.

![Executive revenue by category](Pizza_Report_Images/Executive%20Report/revenue_by_category.png)
![Executive monthly sales revenue](Pizza_Report_Images/Executive%20Report/monthly_sales_revenue.png)
![Executive top 5 best selling pizzas](Pizza_Report_Images/Executive%20Report/top_5_best_selling_pizza_by_revenue.png)

---

### 2. Monthly Report

The Monthly Report allows users to analyse performance for a selected month. In the March view, the business generated **$70.40K revenue**, **1,840 orders**, and **4,261 pizzas sold**. Compared with the previous month, March improved across all major KPIs, with revenue increasing by **8.0%**, orders by **9.2%**, and quantity sold by **7.5%** compared to previous month.

In March, **Classic** and **Chicken** categories each generated approximately **$18K**, while **Veggie** and **Supreme** each contributed around **$17K**. The top pizza by unit sales was **The Barbecue Chicken Pizza** with **231 units**, followed by **The Hawaiian Pizza** with **217 units** and **The Thai Chicken Pizza** with **213 units**.

Weekday revenue was significantly higher than weekend revenue, with approximately **$52.17K** generated on weekdays compared with **$18.23K** on weekends. Daily revenue was generally close to the monthly average of around **$2.3K**, with several above-average days indicating short-term demand spikes.

![March total revenue](Pizza_Report_Images/Monthly%20Report/march_total_revenue.png)
![March top 5 by units sold](Pizza_Report_Images/Monthly%20Report/march_top_5_by_unit_sold.png)
![March daily revenue trend](Pizza_Report_Images/Monthly%20Report/march_daily_revenue.png)
![March weekday vs weekend revenue](Pizza_Report_Images/Monthly%20Report/march_weekday_vs_weekkend_revenue.png)

---

### 3. Time-Based Sales Insights

The Time-Based Sales Insights page focuses on demand patterns over time. Monthly order volume peaked in **July** with approximately **1.94K orders**, while **September** and **October** had the lowest order volumes at around **1.66K orders**. This suggests stronger mid-year demand and weaker early-spring performance.

By weekday, **Friday** recorded the highest order volume at approximately **3.5K orders**, followed by **Thursday and Saturday** at around **3.2K orders**. **Sunday** had the lowest volume at around **2.6K orders**, indicating that demand is strongest toward the end of the working week.

The hourly heatmap shows that order activity is concentrated between **12:00 PM and 8:00 PM**, with the strongest demand generally occurring during lunch and dinner periods. This pattern can support staffing, preparation planning, and inventory management.

The daily order trend with a **7-day moving average** helps smooth short-term variation and identify spikes or drops in daily order activity.

![Total orders by month](Pizza_Report_Images/Time_Based%20sales%20insights/total_orders_by_month.png)
![Order volume by weekday](Pizza_Report_Images/Time_Based%20sales%20insights/order_volumn.png)
![Daily orders trend with moving average](Pizza_Report_Images/Time_Based%20sales%20insights/daily_orders_trend.png)
![Order activity by day and hour](Pizza_Report_Images/Time_Based%20sales%20insights/order_activity_by_hours.png)

---

### 4. Product Insights

The Product Insights page analyses product demand by pizza size, category, and ingredients. The **Classic** category achieved the highest quantity sold with approximately **14.9K units**, followed by **Supreme (12.0K)**, **Veggie (11.6K)**, and **Chicken (11.1K)**.

Pizza size analysis shows that **large (L)** pizzas dominate sales across all categories. For example, the Classic category sold **6,139 large pizzas**, while Veggie sold **5,403 large pizzas**. Extra-large and XXL pizzas had much lower sales volumes, suggesting that regular sizes drive the majority of demand.

Ingredient analysis for the Chicken category shows that **Red Peppers**, **Chicken**, and **Tomatoes** were the most frequently used ingredients. This insight can help with inventory planning by identifying high-demand ingredients that require consistent stock availability.

![Pizza size sales distribution](Pizza_Report_Images/Product%20Insights/size_distribution.png)
![Quantity sold by category](Pizza_Report_Images/Product%20Insights/quantity_sold_by_category.png)
![Top 5 ingredients in chicken category](Pizza_Report_Images/Product%20Insights/top_5_ingredients_by_chicken_category.png)

---

### 5. Operational Performance Analysis

The Operational Performance page examines order behaviour and operational efficiency. The average turnaround time was approximately **11.02 minutes overall** and **11.29 minutes per day**, indicating relatively consistent order preparation performance.

Multi-item orders represented a larger share of total orders than single-item orders. The dashboard shows around **13K single-item orders** and **8K multi-item orders**, with total orders displayed as approximately **21K**. This helps distinguish customer behaviour between simple purchases and larger basket orders.

Turnaround analysis shows that the majority of orders had non-zero turnaround time, with **20,992 non-zero turnaround orders** compared with **358 zero-turnaround orders**. This separation is useful for identifying potential data quality issues or orders requiring further validation.

The price-volume analysis shows a strong negative relationship between average pizza price and total quantity sold, with a correlation coefficient of **-0.95**. This suggests that higher-priced categories tend to sell fewer units, while lower-priced categories have stronger volume performance.

![Average turnaround overall by date](Pizza_Report_Images/Operational%20Performance%20Analysis/average_turnaround_overall.png)
![Single item vs multi item orders](Pizza_Report_Images/Operational%20Performance%20Analysis/single_item_vs_mutiple_item.png)
![Turnaround time breakdown](Pizza_Report_Images/Operational%20Performance%20Analysis/turn_around_breakdown.png)
![Average price-volume relationship](Pizza_Report_Images/Operational%20Performance%20Analysis/average_price_volumn.png)

---

## Main Business Insights

- **Classic pizza is the strongest overall category**, leading both revenue and quantity sold.
- **July is the strongest month**, while September and October show weaker performance.
- **Friday is the busiest weekday**, suggesting stronger end-of-week customer demand.
- **Large pizzas dominate sales**, while XL and XXL sizes have limited demand.
- **Chicken-related pizzas and ingredients are highly important**, especially The Thai Chicken Pizza and The Barbecue Chicken Pizza.
- **Weekday revenue is much higher than weekend revenue**, which may reflect lunch, office, or weekday dining patterns.
- **Average price and quantity sold have a strong negative correlation**, suggesting price sensitivity across pizza categories.
- **Most orders have valid non-zero turnaround times**, while zero-turnaround records should be checked as possible data quality issues.

---

## Dashboard Features

- Interactive page navigation buttons.
- Month selection for monthly performance analysis.
- Top 5 and Bottom 5 ranking toggles.
- Dynamic metric selection between revenue and quantity sold.
- 7-day, 14-day, and 30-day moving average options for time-series smoothing.
- Day-hour heatmap for operational demand analysis.
- KPI cards for quick executive-level summary.

---

## Repository Structure

```text
Pizza-Sales-Analytics-Dashboard/
│
├── README.md
├── Pizza_Sales_Dashboard.pbix
├── data/
│   └── pizza_sales.csv
│
└── Pizza_Report_Images/
    ├── Executive Report/
    │   ├── revenue_by_category.png
    │   ├── monthly_sales_revenue.png
    │   └── top_5_best_selling_pizza_by_revenue.png
    │
    ├── Monthly Report/
    │   ├── march_total_revenue.png
    │   ├── march_top_5_by_unit_sold.png
    │   ├── march_daily_revenue.png
    │   └── march_weekday_vs_weekkend_revenue.png
    │
    ├── Time_Based sales insights/
    │   ├── total_orders_by_month.png
    │   ├── order_volumn.png
    │   ├── daily_orders_trend.png
    │   └── order_activity_by_hours.png
    │
    ├── Product Insights/
    │   ├── size_distribution.png
    │   ├── quantity_sold_by_category.png
    │   └── top_5_ingredients_by_chicken_category.png
    │
    └── Operational Performance Analysis/
        ├── average_turnaround_overall.png
        ├── single_item_vs_mutiple_item.png
        ├── turn_around_breakdown.png
        └── average_price_volumn.png
```

---

## How to Use This Project

1. Download or clone this repository.
2. Open the `.pbix` file in Power BI Desktop.
3. Refresh the dataset if the source file path has changed.
4. Use the page navigation buttons and slicers to explore the dashboard.
5. Review each report page to understand sales, product, time-based, and operational patterns.

---

## Project Outcome

This project demonstrates the ability to design a business-focused Power BI dashboard from transactional sales data. It covers data cleaning, data modelling, DAX measure creation, interactive reporting, and insight communication. The final dashboard supports decision-making across revenue analysis, product performance, demand timing, ingredient planning, and operational monitoring.
