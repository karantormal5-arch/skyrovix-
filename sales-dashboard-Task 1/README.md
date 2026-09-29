# Sales Dashboard - OIBSIP Task

## Overview
A sales dashboard built as a virtual internship project using data analytics concepts in Python (pandas, numpy, matplotlib).

## Dataset
Sample Superstore dataset — 9,994 rows, 21 columns, covering orders from 2014 to 2017.

## Data Preparation
- Checked for missing values and duplicates (none found)
- Converted `Order Date` and `Ship Date` to datetime format
- Created `Year`, `Month`, `Month Name`, and `Year-Month` columns for time-based analysis

## KPIs
- Total Sales: $2,297,200.86
- Total Profit: $286,397.02
- Total Orders: 5,009
- Total Customers: 793
- Profit Margin: 12.47%
- Average Order Value: $458.61

## Charts
1. Monthly Sales Trend (line chart)
2. Sales & Profit by Region (bar chart)
3. Sales by Category (pie chart)
4. Top 10 Products by Sales (horizontal bar chart)

## Filters
Data can be filtered by Region and Category (e.g. West + Technology), with KPIs and charts recalculated for the filtered subset.

## Actionable Insights
1. The West region is the most profitable (Sales ~725K, Profit ~108K). Central has decent Sales (~501K) but the lowest Profit — pricing or cost structure should be reviewed.
2. Technology (~836K) and Office Supplies (~719K) generate higher profit, while Furniture has high Sales but very low Profit (~18K).
3. Tables and Bookcases sub-categories are running at an overall loss — their pricing or discount policy needs to be reconsidered.
4. Discounts above 30% push Profit into negative territory — a discount cap should be set.
5. Sales peak every year in November-December — inventory and promotions should be planned in advance for this period.

## Tools Used
Python, pandas, numpy, matplotlib
