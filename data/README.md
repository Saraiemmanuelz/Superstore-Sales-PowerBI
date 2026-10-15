# Data

**File:** [`Superstore.xlsx`](Superstore.xlsx), sheet `Sample - Superstore`. US retail orders, 3 January 2014 to 30 December 2017.

**Size:** 9,994 order lines and 21 columns, with no missing values and no duplicate rows. Add the original source link and licence here before publishing.

## Columns

Row ID, Order ID, Order Date, Ship Date, Ship Mode, Customer ID, Customer Name, Segment, Country, City, State, Postal Code, Region, Product ID, Category, Sub-Category, Product Name, Sales, Quantity, Discount, Profit.

## KPI reconciliation (dashboard vs source data)

| KPI | Dashboard | Source data | Match |
|---|---|---|---|
| Total Sales | $2.30M | $2,297,200.86 | Yes |
| Total Profit | $286.4K | $286,397.02 | Yes |
| Profit Margin | 12.47% | 12.47% | Yes |
| Total Orders | 5,009 | 5,009 distinct Order IDs | Yes |
| Total Customers | 793 | 793 distinct Customer IDs | Yes |
| Average Order Value | $458.61 | $458.61 | Yes |
| Sales per Customer | $2.90K | $2,896.85 | Yes |
| Total Products | 1,862 | 1,862 distinct Product IDs (1,850 distinct product names) | Yes |
| States / Cities | 49 / 531 | 49 / 531 | Yes |

## Reproducing the report

1. Open the `.pbix` in Power BI Desktop (add it to `dashboard/`).
2. Update the data source path to `data/Superstore.xlsx` (*Transform data → Data source settings*).
