# novamart-analysis
[README (1).md](https://github.com/user-attachments/files/29161149/README.1.md)
# NovaMart: Multi-Channel Retail Analytics (2021–2024)

A simulated end-to-end analyst project for **NovaMart**, a fictional multi-channel retailer operating across Nigeria and Ghana. Built to mirror real analyst work: synthetic data generation, data cleaning, SQL analysis, and a two-dashboard Power BI story — not a tutorial exercise.

## Business Context

NovaMart sells across In-Store, Online, and Marketplace channels in two markets. Leadership wants to understand where growth is coming from, whether it's sustainable, and whether the customer loyalty program is actually working. This project answers both questions using four years of order, payment, customer, and product data.

## Tools & Stack

- **Python** — synthetic data generation
- **Microsoft Excel** — initial data cleaning and validation
- **MySQL Workbench** — SQL analysis on a star schema
- **Power BI** — dashboarding and DAX measures

## Data Model

Star schema with the following tables:

| Table | Type | Purpose |
|---|---|---|
| `orders` | Fact | Order-level transactions |
| `order_items` | Fact | Line-item detail, includes outlier flags |
| `payments` | Fact | Payment method and status |
| `dim_date` | Dimension | Calendar attributes, joins on `full_date` |
| `dim_customers` | Dimension | Customer profile, loyalty tier |
| `dim_products` | Dimension | Product category, pricing |
| `dim_employees` | Dimension | Staff attribution |
| `dim_stores` | Dimension | Store location, channel, market |

**A note on outliers:** rather than deleting anomalous values in `order_items`, each was kept and tagged with `outlier_flag` and `outlier_treatment` columns. The reasoning, and the original values, stay visible — a real analyst documents judgment calls instead of erasing them.

## Workflow

1. Generate realistic synthetic transaction data with Python
2. Clean and validate in Excel (data types, duplicates, missing values)
3. Load into MySQL and build a star schema
4. Write SQL to answer specific business questions (top categories, channel mix, customer segmentation, retention)
5. Build Power BI dashboards around a single narrative each, not a feature checklist

## Dashboards

### 1. Executive Overview
**Story:** NovaMart is growing, but the growth is uneven — Q4 dependency and channel concentration are the two hidden risks.

- Grocery and Sports are the top-performing categories by revenue
- In-Store is the dominant channel, with Online and Marketplace lagging well behind
- Nigeria significantly outperforms Ghana across nearly every metric
- Revenue leans heavily on Q4, raising the question of what happens if that quarter underperforms

<img width="969" height="556" alt="executive-overview" src="https://github.com/user-attachments/assets/3a626a9b-d6a4-4db3-bda5-9b63ac6b9514" />


### 2. Customer Intelligence
**Story:** NovaMart retains customers well, but its loyalty tier system isn't changing customer behaviour.

- Bronze tier dominates both customer headcount and total revenue
- Customer Lifetime Value (CLV) and order frequency are nearly flat across Bronze, Silver, and Gold
- Retention is strong on its own, but the tier structure isn't doing the job of driving customers up the value ladder

<img width="970" height="552" alt="customer-intelligence" src="https://github.com/user-attachments/assets/0ef69a99-57e2-4e4f-a53e-43df8e973d92" />



## Key Recommendations

- Diversify channel investment; over-reliance on In-Store leaves NovaMart exposed if footfall drops
- Build a Q4-independent growth plan — smooth seasonality risk by testing promotions in weaker quarters
- Redesign the loyalty program around behaviour-based incentives (spend thresholds, category-specific rewards) rather than passive tier assignment
- Investigate Ghana's underperformance specifically — is it market size, channel mix, or pricing?

## Repo Structure

```
novamart/
├── data/
│   └── [synthetic CSVs / generation scripts]
├── sql/
│   └── [analysis queries by business question]
├── powerbi/
│   └── [NovaMart.pbix]
├── screenshots/
│   └── [dashboard images]
└── README.md
```

## Author

Oluwabusola Oyenuga — built as part of a data analytics portfolio.
