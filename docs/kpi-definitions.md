# KPI Definitions

Reference definitions for the KPIs shown in the dashboard. Adjust the table and column names in the DAX examples to match your data model.

| KPI | Definition | Dashboard value |
|---|---|---|
| Total Sales | Sum of sales | $2.30M |
| Total Profit | Sum of profit | $286.4K |
| Profit Margin | Total Profit ÷ Total Sales | 12.47% |
| Total Orders | Distinct count of Order ID | 5,009 |
| Total Customers | Distinct count of Customer ID | 793 |
| Average Order Value | Total Sales ÷ Total Orders | $458.61 |
| Sales per Customer | Total Sales ÷ Total Customers | $2.90K |
| Total Products | Distinct count of Product ID | 1,862 |

## Example DAX

```DAX
Total Sales = SUM(FactSales[Sales])
Total Profit = SUM(FactSales[Profit])
Profit Margin = DIVIDE([Total Profit], [Total Sales])
Total Orders = DISTINCTCOUNT(FactSales[Order ID])
Total Customers = DISTINCTCOUNT(FactSales[Customer ID])
Average Order Value = DIVIDE([Total Sales], [Total Orders])
Sales per Customer = DIVIDE([Total Sales], [Total Customers])
```

## Discount Impact page

```DAX
Discount Band =
SWITCH(
    TRUE(),
    FactSales[Discount] = 0, "1. No discount",
    FactSales[Discount] <= 0.2, "2. Up to 20%",
    FactSales[Discount] <= 0.4, "3. 20-40%",
    "4. Over 40%"
)

Avg Discount = AVERAGE(FactSales[Discount])
Lines Over 20% Discount = CALCULATE(COUNTROWS(FactSales), FactSales[Discount] > 0.2)
Profit Over 20% Discount = CALCULATE(SUM(FactSales[Profit]), FactSales[Discount] > 0.2)
Loss-Making Lines % = DIVIDE(CALCULATE(COUNTROWS(FactSales), FactSales[Profit] < 0), COUNTROWS(FactSales))
```

| KPI | Dashboard value |
|---|---|
| Avg Discount | 15.62% |
| Lines Over 20% Discount | 1,393 |
| Profit Over 20% Discount | −$135K |
| Loss-Making Lines % | 18.72% |
