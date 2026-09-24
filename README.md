# Zomato-Style Sales & Revenue Dashboard

An Excel dashboard analyzing ~100,000 food delivery orders (Jan 2024 – Jun 2026) across 12 Indian cities, built to answer key sales and revenue questions using a formula-driven, self-updating design (no hardcoded numbers).

## 📌 Problem Statement

Zomato's food delivery business generates thousands of orders daily across 12 cities, but revenue performance, order cancellations, and customer segments (premium vs. non-premium) aren't tracked in one place — making it hard to spot trends, identify underperforming cities or cuisines, and understand what's driving (or hurting) monthly revenue.

This dashboard consolidates that into a single view to answer:
- How is revenue trending month over month?
- Which cities and cuisines generate the most revenue?
- How do premium members compare to regular customers in spend?
- What's the cancellation rate, and is it a concern?
- Which restaurants are the top revenue drivers?

## 📂 Files in this Repo

| File | Description |
|---|---|
| `Zomato_Sales_Dashboard.xlsx` | The main deliverable — a 3-tab Excel workbook (Dashboard, Summary, Data) |
| `Presentation_Script.md` | A ~12-minute speaker script for presenting the dashboard |
| `data/` | Source CSVs (Fact_Orders, Dim_Customer, Dim_Restaurant, Dim_City, Dim_Date, Dim_Menu, Dim_DeliveryPartner, Fact_OrderItems) *(optional — add if you want raw data included)* |

## 📊 Dataset

A star-schema food delivery dataset:
- **Fact_Orders** (100,000 rows) — one row per order: customer, restaurant, date, subtotal, status
- **Fact_OrderItems** (~200,000 rows) — line items per order
- **Dim_Customer** (10,000) — customer demographics, city, premium status
- **Dim_Restaurant** (2,000) — restaurant name, city, cuisine, rating
- **Dim_Menu** (500) — menu items and prices
- **Dim_DeliveryPartner** (500) — delivery riders
- **Dim_City** (12) — Indian cities covered
- **Dim_Date** (912) — date dimension with weekend/season/festival flags

Data quality: no missing values, ~95% of orders delivered, ~5% cancelled.

## 🖥️ Dashboard Structure

- **Dashboard tab** — KPI cards (Total Revenue, Delivered Orders, AOV, Cancellation Rate, Premium Revenue Share) + 6 charts: monthly revenue trend, revenue by city, revenue by cuisine, top 10 restaurants, premium vs. non-premium, weekday vs. weekend.
- **Summary tab** — every aggregation as a live `SUMIFS`/`COUNTIFS` formula referencing the Data tab.
- **Data tab** — the 100,000-row flattened order table (orders joined with customer, restaurant, and date attributes), the single source of truth for every number in the workbook.

## 🔑 Key Findings

- Revenue is flat month-over-month (~₹2.7M–3.1M), with a consistent **February dip** and **December peak** every year.
- **Lucknow** leads city revenue (₹9.24M); **Pune** is lowest (₹5.78M) — driven by order volume, not AOV (which is nearly identical across all cities).
- Revenue is spread evenly across **cuisines** (Chinese 34%, Indian 33%, Italian 33%) and **restaurants** — the top 10 restaurants account for only ~6% of total revenue (no 80/20 concentration).
- **Premium members** (~10% of customers) generate ~10% of revenue with near-identical AOV to non-premium customers — premium status doesn't correlate with higher spend in this data.
- **Cancellation rate** is ~5%, within normal range for food delivery, and stable across cities, cuisines, and months.

