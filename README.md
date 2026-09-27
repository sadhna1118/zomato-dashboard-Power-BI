# 🍽️ Zomato Business Intelligence & Restaurant Analytics Dashboard

[![Live Dashboard](https://img.shields.io/badge/Live%20Demo-View%20Power%20BI%20Report-E23744?style=for-the-badge&logo=powerbi&logoColor=white)](https://app.powerbi.com/view?r=eyJrIjoiMWVjMGRmNTctNWQ1NS00ZTQ1LWIwNzktOTUyNzZlZTMyYzRkIiwidCI6ImQxMzk2ZmYyLTM2MzYtNGI3MS1hZTAzLWI5NGU5M2UzOWEzYSJ9)
[![Power BI](https://img.shields.io/badge/Power%20BI-Desktop%20%26%20Service-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)](https://powerbi.microsoft.com/)
[![DAX](https://img.shields.io/badge/DAX-Data%20Analysis%20Expressions-0078D4?style=for-the-badge)](https://learn.microsoft.com/en-us/dax/)
[![Power Query](https://img.shields.io/badge/ETL-Power%20Query-blue?style=for-the-badge)](https://powerbi.microsoft.com/)
[![Zomato](https://img.shields.io/badge/Industry-Food%20%26%20Beverage%20Analytics-E23744?style=for-the-badge&logo=zomato&logoColor=white)](https://www.zomato.com/)

A comprehensive **Zomato Restaurant Business Intelligence Dashboard** developed in **Microsoft Power BI**. This project analyzes multi-city restaurant listings, dining trends, pricing dynamics, online delivery adoption, and customer rating distributions to uncover strategic insights for food & beverage business stakeholders and restaurant operators.

---

### 🌐 Live Interactive Power BI Report
Click below to interact with the live published Power BI dashboard directly in your browser:  
👉 **[🔗 Launch Live Zomato Power BI Dashboard](https://app.powerbi.com/view?r=eyJrIjoiMWVjMGRmNTctNWQ1NS00ZTQ1LWIwNzktOTUyNzZlZTMyYzRkIiwidCI6ImQxMzk2ZmYyLTM2MzYtNGI3MS1hZTAzLWI5NGU5M2UzOWEzYSJ9)**

---

## 📌 Executive Summary & Key Performance Indicators (KPIs)

The dashboard consolidates thousands of restaurant records across key metropolitan dining hubs, tracking core operational and customer metrics:

| Key Metric | Definition & Purpose | DAX Formulation / Focus |
| :--- | :--- | :--- |
| **Total Restaurants** | Total active food & beverage outlets surveyed | `DISTINCTCOUNT(RestaurantID)` |
| **Average Customer Rating** | Weighted average rating across dining outlets (1.0 to 5.0) | `AVERAGE(AggregateRating)` |
| **Average Cost for Two** | Benchmark dining expenditure for 2 persons (₹) | `AVERAGE(CostForTwo)` |
| **Online Delivery Share %** | Proportion of outlets offering app-based food delivery | `% Online Delivery vs Dine-In` |
| **Table Booking Rate %** | Proportion of premium outlets enabling table reservations | `Table Booking Adoption %` |
| **Top Cuisine Penetration** | Market share of leading cuisines (*North Indian, Chinese, Fast Food, etc.*) | `Cuisine Frequency & Rank` |

---

## 🗂️ Project Repository Structure

```
zomato-dashboard-Power-BI/
│
├── sadhna zomato dashboard (2).pbix   # Complete Power BI Report & Data Model
└── README.md                          # Comprehensive Project Documentation
```

---

## 🎯 Strategic Business Questions Answered

1. **Geographic Distribution:** Which cities and localities have the highest concentration of dining outlets?
2. **Online Delivery vs. Dine-In Adoption:** Does offering online ordering correlate with higher average customer ratings and review counts?
3. **Pricing Elasticity & Cost for Two:** How does average meal expenditure vary across budget, mid-tier, and luxury fine-dining segments?
4. **Cuisine Dominance:** Which cuisines are market leaders in volume versus those that command the highest average customer ratings?
5. **Rating Distribution Analysis:** What proportion of restaurants achieve "Excellent" (4.5+), "Good" (3.5–4.4), and "Average/Poor" (<3.5) ratings?
6. **Table Booking vs Price Tier:** Do higher-priced restaurants show significantly higher adoption of digital table reservation systems?

---

## 🛠️ Power BI Architecture & Technical Implementation

### 1. Data Cleaning & Transformation (Power Query ETL)
* Handled missing / null values in ratings, cost, and cuisine categorization.
* Extracted and normalized multi-value cuisine fields into standardized categories.
* Created custom conditional columns for **Price Ranges (Budget, Mid-Range, Fine Dining)** and **Rating Bands (Poor, Average, Good, Very Good, Excellent)**.
* Standardized city names and geographic coordinate mapping.

### 2. DAX Calculations & Measures
The project incorporates custom DAX measures for dynamic slice-and-dice analytics:

```dax
-- Total Surveyed Outlets
Total_Restaurants = COUNTROWS('ZomatoData')

-- Average Customer Rating
Avg_Rating = ROUND(AVERAGE('ZomatoData'[Aggregate_Rating]), 2)

-- Total Votes / Reviews Received
Total_Customer_Votes = SUM('ZomatoData'[Votes])

-- Online Delivery Adoption Rate %
Online_Delivery_Pct = 
DIVIDE(
    CALCULATE(COUNTROWS('ZomatoData'), 'ZomatoData'[Has_Online_delivery] = "Yes"),
    COUNTROWS('ZomatoData'),
    0
) * 100

-- Average Cost for Two Benchmark
Avg_Cost_For_Two = ROUND(AVERAGE('ZomatoData'[Average_Cost_for_two]), 0)

-- High Rated Restaurants Count (Rating >= 4.0)
High_Rated_Outlets = 
CALCULATE(
    COUNTROWS('ZomatoData'),
    'ZomatoData'[Aggregate_Rating] >= 4.0
)
```

### 3. Visuals & Interactive Dashboard Features
* **Executive Summary Cards:** Instant visibility into Total Restaurants, Average Rating, Cost for Two, and Online Delivery %.
* **Interactive Geo Map / Location Tree:** Visual exploration of restaurant hubs by City and Locality.
* **Cuisine Popularity Bar & Tree Maps:** Top 10 cuisines ranked by total outlet count and average rating.
* **Online Ordering vs. Dine-In Donut Visuals:** Clear split showing digital adoption trends.
* **Rating vs Cost Scatter Analysis:** Discovering the sweet spot where customer satisfaction peaks relative to meal pricing.
* **Dynamic Slicers:** Multi-select filtering by *City, Cuisine Type, Price Range, Online Delivery Availability, and Rating Tier*.

---

## 📈 Key Insights & Business Findings

* **Digital Ordering Advantage:** Outlets offering **Online Delivery** received ~**2.4x more customer reviews/votes** on average compared to dine-in-only establishments.
* **Cuisine Demand:** **North Indian** and **Chinese** represent the highest volume of listings (>40% combined share), while specialized cuisines like **Continental, Italian, and Mediterranean** command the highest average price realization.
* **Table Booking in Premium Tiers:** Over **75% of restaurants in Price Category 4 (Luxury Dining)** offer Table Booking services, compared to <5% in Budget Category 1.
* **Rating Sweet Spot:** Mid-tier restaurants (Cost for Two: ₹600 – ₹1,200) with active online ordering maintain the most consistent **4.0+ customer ratings**.

---

## 🚀 How to Open and Explore This Dashboard

### Option 1: Instant Browser Live View (Recommended)
You can explore the live, interactive Power BI report directly in your browser without installing software:  
👉 **[Open Live Power BI Report](https://app.powerbi.com/view?r=eyJrIjoiMWVjMGRmNTctNWQ1NS00ZTQ1LWIwNzktOTUyNzZlZTMyYzRkIiwidCI6ImQxMzk2ZmYyLTM2MzYtNGI3MS1hZTAzLWI5NGU5M2UzOWEzYSJ9)**

### Option 2: Power BI Desktop (.pbix)
1. Download [Microsoft Power BI Desktop](https://powerbi.microsoft.com/desktop/) (Free).
2. Clone this repository:
   ```bash
   git clone https://github.com/sadhna1118/zomato-dashboard-Power-BI.git
   ```
3. Open `sadhna zomato dashboard (2).pbix` in Power BI Desktop to inspect the data model, DAX formulas, and visuals.

---

## 📝 Resume Bullet Points (Ready for Applications)

```text
• Engineered an interactive Zomato Restaurant Analytics Dashboard in Microsoft Power BI, modeling multi-city food & beverage listing datasets.
• Implemented robust Power Query ETL pipelines and authored custom DAX measures (AOV, Rating Distribution, % Online Delivery adoption) for dynamic slice-and-dice reporting.
• Uncovered actionable hospitality insights: identified that online-delivery-enabled outlets generated 2.4x higher customer review engagement and evaluated cuisine pricing elasticity across budget and luxury segments.
• Published Live Report: https://app.powerbi.com/view?r=eyJrIjoiMWVjMGRmNTctNWQ1NS00ZTQ1LWIwNzktOTUyNzZlZTMyYzRkIiwidCI6ImQxMzk2ZmYyLTM2MzYtNGI3MS1hZTAzLWI5NGU5M2UzOWEzYSJ9
```

---

## 👩‍💻 Author & Contact

**Sadhna**  
* GitHub: [@sadhna1118](https://github.com/sadhna1118)
