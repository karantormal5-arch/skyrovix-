# Customer Analytics Dashboard (Power BI)

Customer analytics project built during the Skyrovix Data Analyst virtual internship.
The dashboard analyses customer behaviour: repeat purchases, customer segments, country
spread, and monthly revenue trend.

## Data source
The organisation did not provide a separate customer file, so the public
**Online Retail** transactional dataset is used (541,909 rows, 1 Dec 2010 to 9 Dec 2011).
The raw file is not included in this repository.

## Data preparation
`data_cleaning.py` applies these steps in order:
1. Remove duplicate rows
2. Remove rows with blank Description or CustomerID
3. Remove cancelled invoices (InvoiceNo starting with C)
4. Remove rows with zero or negative Quantity or UnitPrice
5. Remove non-product codes (POST, M, C2, DOT, BANK CHARGES, PADS)
6. Create Revenue (Quantity x UnitPrice) and InvoiceMonth

Result: 391,150 transaction rows, 18,402 invoices, 4,334 customers, GBP 8,737,227.64 revenue.

It also builds `customer_summary.csv` with one row per customer (orders, revenue,
segment, repeat flag, order bucket).

## KPIs
| KPI | Definition | Value |
|---|---|---|
| Total Revenue | Sum of Revenue | GBP 8.74M |
| Total Orders | Distinct InvoiceNo | 18,402 |
| Total Customers | Distinct CustomerID | 4,334 |
| Average Order Value | Total Revenue / Total Orders | GBP 474.80 |
| Repeat Customer % | Customers with more than 1 order / Total Customers | 65.3% |
| Avg Orders per Customer | Mean of Orders | 4.25 |
| Avg Revenue per Customer | Mean of TotalRevenue | GBP 2,016 |

## Dashboard
- Slicers: Country, Segment, Orders range
- Charts: Top 10 customers by revenue, revenue by segment, customers by country,
  monthly revenue trend, customers by order frequency
- Key insights are shown on the dashboard

## How to run
1. Install Python 3 and pandas: `pip install pandas`
2. Put `OnlineRetail.csv` in a folder.
3. Run: `python data_cleaning.py --input OnlineRetail.csv --outdir output`
   (or open `data_cleaning.ipynb` in Jupyter and run all cells)
4. Open `Customer_Analytics_Dashboard.pbix` in Power BI Desktop and load
   `output/OnlineRetail_clean.csv` and `output/customer_summary.csv` (Get data > Text/CSV).

## Files
- `data_cleaning.py`: cleaning and customer summary script (run from the command line)
- `data_cleaning.ipynb`: same cleaning steps as a Jupyter notebook, for step-by-step review
- `Customer_Analytics_Dashboard.pbix`: Power BI dashboard
- `Customer_Analytics_Dashboard_Documentation.pdf`: full project documentation
- `dashboard.png`: dashboard screenshot

## Limitations
- Rows with blank CustomerID are excluded (about 25% of raw rows).
- December 2011 is partial (data ends 9 Dec 2011).
- A few customers have very high revenue from few orders; these are kept and flagged.
