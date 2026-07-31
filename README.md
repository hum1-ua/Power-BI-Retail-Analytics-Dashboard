# Power BI Retail Analytics Dashboard

## Overview
This project is an interactive business intelligence dashboard developed with Microsoft Power BI to analyse sales, customers, products and geographical performance in an online retail business.

The main objective of the project was to learn how to transform raw transactional data into meaningful business insights and develop a dashboard that could support data-driven decision-making.

The project uses the Online Retail II dataset, containing transactional data from an online retail business for 2010 and 2011. 
https://archive.ics.uci.edu/dataset/502/online+retail+ii

## Project Objectives
The dashboard was designed to answer key business questions such as:

- How are sales performing compared with the previous year?
- How many orders and active customers does the business have?
- Which customers generate the most revenue?
- Which customer segments are the most valuable?
- Which products generate the highest sales?
- What is the impact of returns on revenue?
- Which countries generate the most sales?
- How is the business performing across different markets?
- What is the relationship between product volume and revenue?

## Dashboard Structure

The report is divided into four analytical areas.

### 1. Executive Summary
![Executive Summary](pages/executive_summary-1.png)

Provides a high-level overview of business performance through:

- Total Sales
- Total Orders
- Average Order Value
- Active Customers
- Year-over-Year performance
- Monthly sales comparison between 2010 and 2011

This page is designed to provide management with a quick overview of the company's performance.

### 2. Customer Analytics
![Product and Sales](/pages/customer_analytics-1.png)
Focuses on customer behaviour and value.

It includes:

- Average Spend per Customer
- Orders per Customer
- Recurring Customers
- Top Customers by Sales
- Customer Revenue Distribution
- Customer Segmentation using RFM analysis
- Relationship between Orders per Customer and Total Sales

The RFM segmentation helps classify customers according to:

- Recency
- Frequency
- Monetary Value

Customer groups include Champions, Loyal Customers, Potential Loyalists, New Customers, At Risk, Hibernating and other segments.

### 3. Product & Sales Analytics
![Product and Sales](/pages/product_analytics-1.png)
Analyses product performance and sales quality.

The page includes:

- Returned Sales
- Returned Orders
- Return Rates
- Shipping Charges
- Top Products by Sales
- Product Volume vs Revenue

This section helps identify high-performing products while also providing visibility into returns and shipping-related costs.

### 4. Geographic & Market Analytics
![Product and Sales](/pages/geographic_analytics.png)

Provides a geographical view of the business.

It includes:

- International Sales
- Countries Served
- Global Sales Distribution
- Sales by Country
- Active Customers by Country
- Orders by Country
- Average Order Value by Country

This allows the user to identify the most important markets and compare their commercial performance.

## Data Model

The project follows a simple star-schema approach, separating transactional data from the date dimension.


## Key Measures

Some of the main DAX measures created for the dashboard include:

- Total Sales
- Total Orders
- Active Customers
- Average Order Value
- Previous Year Sales
- Sales YoY %
- Orders YoY %
- Customers YoY %
- Returned Sales
- Returned Orders
- Return Rate %
- Shipping Charges
- RFM Customer Segmentation

Example:

```DAX
Total Sales =
SUMX(
    'Fact_Sales',
    'Fact_Sales'[Quantity] * 'Fact_Sales'[Price]
)
```
## Key Insights

### Executive Summary
- Sales dropped 3.4% YoY while orders fell more sharply (-12.9%), but Average Order Value rose 8.9%. This suggests the business is retaining fewer customers, but each purchase carries more value — pointing toward a retention-focused strategy rather than pure acquisition.
- December shows a sharp drop compared to November, but this reflects an incomplete month in the dataset (data ends 09/12/2011), not an actual demand collapse.

### Customer Analytics
- 68.9% of customers are recurrent, a strong retention rate for an online retail business.
- "Champions" is the largest segment (22.55%), but "Hibernating," "At Risk," and "Can't Lose Them" together account for almost 40% of the customer base — a clear opportunity for win-back campaigns.
- The Orders vs Sales scatter plot shows a small group of high-order customers driving disproportionately high revenue, likely wholesale or B2B buyers rather than typical end consumers.

### Product & Sales Analytics
- The order return rate (22%) is far higher than the revenue return rate (7.34%), indicating that returns are concentrated in low-value orders rather than high-value purchases.
- Shipping charges represent only 2.23% of total sales, a relatively low operating cost.
- The Product Volume vs Revenue scatter shows a classic long-tail pattern: most products cluster in low volume/low revenue, while a handful of high-volume products drive a disproportionate share of income.

### Geographic & Market Analytics
- The United Kingdom dominates the business, accounting for the vast majority of sales and active customers — expected for a UK-based retailer, but it also signals a concentration risk.
- Outside the UK, countries like the Netherlands, Australia, and Denmark show the highest Average Order Value (>$1,600), suggesting large but infrequent orders — likely wholesale/distributor buyers rather than individual consumers.
- International sales represent 15.1% of total revenue across 43 countries, showing wide geographic reach but shallow penetration outside the domestic market.
