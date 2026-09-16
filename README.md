

The dashboard answers a few core business questions:

- How much are we selling, and how much of it is actually profit?
- Which months are losing money?
- Which categories, sub-categories and states drive volume and margin?
- How do customers prefer to pay?
- Who are the highest-value customers?

Everything is filterable by quarter, so seasonal patterns can be isolated without rebuilding views.

---

## Key Metrics

| KPI | Value |
|---|---|
| Sum of Amount | 438K |
| Sum of Profit | 37K |
| Sum of Quantity | 5,615 |
| Sum of AOV | 121K |

Overall margin sits at roughly **8.4%** of total sales.

---

## Visuals

**Profit–Loss by Month** — Column chart tracking monthly profit. January through April are the strongest stretch, November peaks again, while May, July, September and December fall into loss. Useful for spotting discount-heavy or return-heavy periods.

**Top States** — Bar chart of sales by state. Maharashtra leads, followed by Madhya Pradesh, Uttar Pradesh, Delhi and Rajasthan.

**Quantity by Category** — Donut chart of unit share:

| Category | Share |
|---|---|
| Clothing | 63% |
| Electronics | 21% |
| Furniture | 17% |

**Quantity by Payment-Mode** — Donut chart of how orders are paid for:

| Mode | Share |
|---|---|
| COD | 44% |
| UPI | 21% |
| Debit Card | 13% |
| Credit Card | 12% |
| EMI | 10% |

Cash on delivery still dominates, which has direct implications for working capital and return rates.

**Profit by Sub-Category** — Ranked bar chart. Printers and Bookcases are the top margin contributors, ahead of Saree, Accessories and Tables.

**Top Customers** — Bar chart of the five highest-spending customers by total amount.

**Quarter Slicer** — Tile slicer (Qtr 1–4, plus Select All) and a dropdown filter wired to every visual on the page.

---

## Dataset

The source data is a transactional sales table. Expected fields:

| Field | Description |
|---|---|
| `Order ID` | Unique order identifier |
| `Order Date` | Date of purchase (drives the month/quarter hierarchy) |
| `Customer Name` | Buyer name |
| `State` / `City` | Delivery location |
| `Category` | Clothing, Electronics, Furniture |
| `Sub-Category` | Printers, Bookcases, Saree, Accessories, Tables, etc. |
| `Quantity` | Units sold |
| `Amount` | Order value |
| `Profit` | Profit on the order |
| `Payment Mode` | COD, UPI, Debit Card, Credit Card, EMI |

---

## Measures

Core DAX measures used in the report:

```dax
Total Sales = SUM(Orders[Amount])

Total Profit = SUM(Orders[Profit])

Total Quantity = SUM(Orders[Quantity])

AOV = DIVIDE([Total Sales], DISTINCTCOUNT(Orders[Order ID]))

Profit Margin % = DIVIDE([Total Profit], [Total Sales])
```

---

## Getting Started

1. Clone or download this repository.
2. Open `Product_Sales_Analysis_Dashboard.pbix` in **Power BI Desktop** (free download from Microsoft).
3. If the data source path has changed, go to **Transform Data → Data source settings** and point it at your local copy of the dataset.
4. Click **Refresh**.

---

## Tools Used

- **Power BI Desktop** — data model, DAX measures, report design
- **Power Query** — cleaning, type casting, column derivation
- **Excel / CSV** — source data

---

## Insights

- Clothing accounts for nearly two-thirds of units sold but does not dominate profit, so volume and margin are decoupled.
- Four of twelve months run at a loss, which drags the annual margin down to single digits. Investigating discounting and returns in those months is the highest-leverage fix.
- A 44% COD share ties up cash and raises return exposure compared to prepaid orders.
- Sales are concentrated in a handful of states, leaving clear room for geographic expansion.

---

## Possible Extensions

- Year-over-year comparison and running totals
- Customer segmentation (RFM) and retention analysis
- Return rate by category and payment mode
- Drill-through pages for individual states and customers
- Publish to Power BI Service with a scheduled refresh

---

## Author

Built as a data analytics portfolio project.
