# Retail Sales & Customer Behaviour Analysis: Monthly Trends, Product Performance & Geographic Insights

## Overview

This project analyses transactional sales and customer data from a US-based retail business operating across multiple states. Using SQL, the analysis examines monthly sales performance, product-level revenue, customer purchasing behaviour, and geographic demand patterns to answer a core business question:

> Which customers, products, and locations generate the highest revenue and order volume — and what does that mean for marketing, pricing, and retention strategy?

The analysis was conducted using SQLite (SQLiteStudio) across a relational database containing monthly sales tables and a customer accounts table.

The SQL code used for this analysis is available in:
- `customer_oders_analysis.sql`

---

# Table of Contents

- [Dataset](#dataset)
- [Analysis](#analysis)
  - [Data Quality & Validation](#1-data-quality--validation)
  - [Monthly Order Volume](#2-monthly-order-volume)
  - [Product Performance](#3-product-performance)
  - [Customer Behaviour](#4-customer-behaviour)
  - [Geographic Analysis](#5-geographic-analysis)
- [Executive Summary](#executive-summary)
- [Recommendations](#recommendations)
- [Limitations](#limitations)

---

# Dataset

The dataset is structured as a relational database (`BIT_DB`) containing multiple monthly transaction tables and a customer accounts table.

## Tables Used

- `JanSales`
- `FebSales`
- `AprSales`
- `MaySales`
- `customers`

## Key Metrics Available Per Transaction

| Field | Description |
|---|---|
| `orderid` | Unique transaction identifier |
| `product` | Product purchased |
| `quantity` | Units sold |
| `price` | Unit selling price |
| `location` | Full customer/store address |
| `orderdate` | Date and time of purchase |
| `acctnum` | Customer account number |

📌 **Note:**  
This dataset required data-quality filtering prior to analysis. Invalid order IDs and duplicated header rows were excluded from calculations to ensure reporting accuracy.


---

# Analysis

## 1. Data Quality & Validation

Before analysis began, the dataset was assessed for integrity issues.

Two validation filters were consistently applied throughout the project:

```sql
WHERE length(orderid) = 6
AND orderid <> 'Order ID'
```

These filters ensured:
- malformed or truncated order IDs were excluded
- duplicated header rows accidentally imported into the dataset were removed
- all calculations reflected valid transactional records only

This demonstrates awareness of real-world data-quality issues commonly encountered in operational datasets.

📸 *[Insert screenshot: row count before and after filtering]*

---

## 2. Monthly Order Volume

The first stage of analysis examined overall order activity in January.

The analysis measured:
- total January orders
- iPhone-specific order counts
- high-demand product concentration

The iPhone represented a significant proportion of January order volume, positioning it as one of the highest-demand products during the analysed period.

### Business Value

Understanding monthly order concentration supports:
- inventory forecasting
- demand planning
- product performance monitoring
- seasonal sales analysis

📸 *[Insert screenshot: January order volume query result]* 

---

## 3. Product Performance

### Revenue by Product — January

Revenue was calculated by multiplying:

```sql
quantity * price
```

Results were aggregated at product level to identify:
- highest-revenue products
- low-performing products
- pricing differences across product categories

The analysis identified the highest-revenue product in January based on total sales value.

### Cheapest Product — January

The project also identified the lowest-priced product sold during January to better understand product pricing distribution.

### Headphone Category Performance — February

Headphone-related products were isolated using product filtering logic to evaluate category-level sales volume.

### Business Value

Product-level revenue analysis supports:
- pricing strategy
- product prioritisation
- inventory planning
- category performance evaluation
- merchandising decisions

📸 *[Insert screenshot or chart: revenue by product]*

---

## 4. Customer Behaviour

### February Customer Accounts

Distinct customer account numbers were retrieved for all February transactions by joining sales and customer reference tables.

### Average Order Value — February

Average transaction revenue was calculated using:

```sql
AVG(quantity * price)
```

This established a baseline measure of customer spending behaviour.

### Bulk Purchaser Analysis

Customers purchasing more than two products in a single transaction were isolated as a high-value customer segment.

The analysis measured:
- number of high-volume purchasers
- average spend for bulk purchasers
- purchasing behaviour differences relative to general customers

### Business Value

Customer-level behavioural analysis supports:
- loyalty programme development
- customer segmentation
- targeted promotions
- retention strategy development
- basket-size optimisation

📸 *[Insert screenshot: bulk purchaser query result]*

---

## 5. Geographic Analysis

### Seattle Location-Level Sales

The project examined sales activity at:

```text
548 Lincoln St, Seattle, WA 98101
```

The analysis identified:
- products sold at this location
- units sold
- revenue generated per product

### Georgia High-Value Orders — April

Orders from Georgia where the average item price exceeded $1,000 were isolated to identify regions associated with premium purchasing behaviour.

### Business Value

Geographic analysis supports:
- regional inventory allocation
- territory performance benchmarking
- localised marketing initiatives
- operational planning decisions

📸 *[Insert screenshot: Georgia high-value orders query result]*

---

# Executive Summary

| Metric | Insight |
|---|---|
| January order activity | Strong overall transaction volume |
| iPhone demand | One of the highest-demand products |
| Highest-revenue product | Significant revenue concentration observed |
| Average February order value | Established customer spending baseline |
| Bulk purchaser behaviour | Higher average spend than standard customers |
| Geographic demand | Premium purchasing concentrated in selected regions |

## Key Findings

- Product revenue was concentrated among a limited number of high-performing products.
- Bulk purchasers represented a smaller but higher-value customer segment.
- Geographic purchasing behaviour varied across locations and states.
- Data quality filtering was necessary to ensure analytical accuracy.
- Product category demand differed significantly across product groups.

---

# Recommendations

## Products
- Prioritise inventory planning for high-revenue products.
- Review low-performing products for repositioning or discontinuation.
- Expand monitoring of category-level demand trends.

## Customers
- Develop incentives targeting high-volume purchasers.
- Introduce retention analysis across future months.
- Build customer segmentation models using purchasing behaviour.

## Operations
- Automate upstream data validation processes.
- Expand geographic aggregation to city and state levels for more actionable reporting.
- Standardise data-cleaning rules across reporting workflows.

---

# Limitations

- The dataset covers selected months only rather than a full annual period.
- Customer demographic information was unavailable.
- Profitability could not be analysed because cost data was not provided.
- Geographic analysis operated primarily at address level rather than regional hierarchy level.
- Time-series trend analysis was limited due to incomplete monthly coverage.

---

# SQL Techniques Demonstrated

- `SELECT`
- `WHERE`
- `GROUP BY`
- `ORDER BY`
- `HAVING`
- `DISTINCT`
- `INNER JOIN`
- `LEFT JOIN`
- aggregate functions (`SUM`, `AVG`, `COUNT`, `MIN`)
- filtering logic
- subqueries
- pattern matching using `LIKE`

---

# Repository Structure

```text
customer-orders-analysis/
├── README.md
├── sql_queries.sql
├── screenshots/
└── visuals/
```

---

# Tools Used

- SQLiteStudio
- SQL
- GitHub
