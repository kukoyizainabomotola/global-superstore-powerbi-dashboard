# Global Superstore Executive Dashboard (Power BI)

An interactive Power BI dashboard that turns raw retail order data into clear insights on sales, profit, customers, products and regional performance.

Built as the **Week 2 Business Analytics Case Study** of the **AnalystLab Africa Data Analytics Internship Programme**.

![Dashboard overview](images/dashboard.png)

---

## Business problem

A national retail company wants an executive dashboard that lets management monitor sales performance, profitability, customer behaviour and regional performance, and decide where to act. This project prepares the data, builds the dashboard in Microsoft Power BI, and recommends actions based on the findings.

### Business questions answered

1. What is the overall sales performance of the company?
2. Which regions generate the highest sales and profit?
3. Which customer segments contribute the most revenue?
4. Which product categories perform best?
5. Which products are the most profitable?
6. What trends can be observed over time?
7. What should management do to improve performance?

---

## Dataset

| Item | Detail |
|---|---|
| Source | [Global Super Store Dataset (Kaggle)](https://www.kaggle.com/datasets/apoorvaappz/global-super-store-dataset) |
| Size | 51,290 order lines, 24 columns, 25,035 unique orders |
| Period | 2011 to 2014 |
| Coverage | 7 markets, 3 customer segments, 3 product categories, 17 sub-categories |
| Key fields | Order Date, Market, Country, Segment, Category, Sub-Category, Product Name, Sales, Quantity, Discount, Profit, Shipping Cost |

---

## Tools used

- Microsoft Power BI Desktop (Power Query and DAX)
- Excel / CSV for the source data
- Word for the written reports

---

## Data preparation (Power Query)

- Imported the CSV using the Western European (1252) file origin, since the file is not UTF-8.
- Profiled the data on the full dataset. Only **Postal Code** had missing values (about 80% empty, because most countries outside the US have none), so it was removed.
- Converted Order Date and Ship Date from text (`dd-mm-yyyy`) to proper dates using the English (United Kingdom) locale.
- Set correct data types: Sales, Profit, Discount and Shipping Cost as decimals, Quantity as a whole number, Row ID as text.
- Trimmed and cleaned all text columns.
- Checked for duplicates: none found. Repeated Order ID and Product ID pairs are separate order lines, so they were kept.
- Added helper columns: Year, Month Number and Month Name.

---

## DAX measures

```DAX
Total Sales   = SUM(Orders[Sales])
Total Profit  = SUM(Orders[Profit])
Total Orders  = DISTINCTCOUNT(Orders[Order ID])
Average Sales = DIVIDE([Total Sales], [Total Orders])
Profit Margin = DIVIDE([Total Profit], [Total Sales])
```

Average Sales is calculated per order. `DISTINCTCOUNT` is used for Total Orders because one order contains several lines.

---

## Dashboard features

- **5 KPI cards:** Total Sales, Total Profit, Total Orders, Average Sales per Order, Profit Margin
- **13 visuals on one page:** 2 bar charts, 2 column charts, a line chart, a donut chart, a filled map, a matrix and the KPI cards
- **3 slicers:** Year, Market and Customer Segment, which filter every visual
- A consistent maroon and tan theme (`Maroon_Executive_Theme.json`)

### Headline KPIs

| Total Sales | Total Profit | Total Orders | Avg Sales per Order | Profit Margin |
|---|---|---|---|---|
| $12.64M | $1.47M | 25,035 | $505 | 11.6% |

---

## Key insights

1. **Overall performance is healthy:** $12.64M in sales and $1.47M in profit at an 11.6% margin.
2. **APAC leads on both sales ($3.59M) and profit ($0.44M).** APAC, EU and the US together give about 70% of sales.
3. **Technology is the strongest category** ($4.74M sales, 14.0% margin). Furniture sells $4.11M but earns only a 6.9% margin.
4. **Consumers contribute 51.5% of sales**, followed by Corporate (30.3%) and Home Office (18.3%), with similar margins.
5. **Sales grew about 90% from 2011 to 2014**, with a year-end peak, while the margin stayed flat at about 11% to 12%.

## Risks

- Tables lose money overall (about -$64K on $757K of sales).
- EMEA earns only a 5.4% margin and Africa has low profit relative to sales.
- Furniture's low margin and heavy dependence on APAC, EU and the US.

## Opportunities

- Grow Technology, especially Copiers and Phones.
- Expand in APAC and EU, and test growth in Canada (26.6% margin on a small base).
- Win more Corporate and Home Office customers and prepare for the November to December peak.

## Recommendations

1. Reprice, renegotiate or discontinue Tables.
2. Investigate pricing, shipping and discounts in EMEA and Africa.
3. Cap and approve deep discounts (order lines discounted 50% or more lost about $571K in the underlying data).
4. Prioritise Technology and stock up before the year-end peak.
5. Invest in APAC and EU and pilot growth in Canada.
6. Improve Furniture margins and run targeted offers for Corporate and Home Office customers.

---

## Repository structure

```
global-superstore-powerbi-dashboard/
├── README.md
├── data/
│   └── Global_Superstore2.csv
├── dashboard/
│   ├── Global_Superstore_Dashboard.pbix
│   ├── Maroon_Executive_Theme.json
│   └── Dashboard_Export.pdf
├── images/
│   └── dashboard.png
└── reports/
    ├── BI_Overview_Report_Global_Superstore.docx
    └── Executive_Summary_Report_Global_Superstore.docx
```

## How to open the dashboard

1. Download `Global_Superstore_Dashboard.pbix` from the `dashboard` folder.
2. Open it in [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free, Windows).
3. Use the Year, Market and Customer Segment slicers to explore the data.

If Power BI asks for the data source, point it to `data/Global_Superstore2.csv` and choose the Western European (1252) file origin.

---

## Skills developed

Data cleaning and transformation in Power Query, DAX measures, KPI design, data visualisation, dashboard layout and theming, business analysis, and writing executive-level insights and recommendations.

---

## Author

**Kukoyi Zainab Omotola**
AnalystLab Africa Data Analytics Internship, Week 2

LinkedIn: [Kukoyi Zainab Omotola](https://www.linkedin.com/in/zainab-kukoyi-060982419)

#AnalystLabAfrica
