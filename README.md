# SQL Sales Analysis and Customer Insights

A SQL Server portfolio project focused on exploring sales performance, product trends, and customer purchasing behaviour. The project uses SQL queries, common table expressions (CTEs), joins, aggregate functions, and window functions to turn transaction-level data into business-focused reports.

> **Project background:** This project was built by following a SQL data analyst portfolio tutorial and practising the techniques demonstrated in it. The repository documents that learning project and the analyses implemented in the SQL script.

## Project objectives

The goal is to practise answering practical business questions with SQL, including:

- How do sales, customer counts, and quantities change over time?
- How do products perform compared with their own average sales and the previous year?
- How are products distributed across cost ranges?
- How can customers be grouped by spending and purchasing history?
- Which product categories contribute the most to overall sales?
- Which customer and product metrics are useful in summary reports?

## Tools and technologies

- **Microsoft SQL Server** — database engine
- **SQL Server Management Studio (SSMS)** — query development and execution
- **T-SQL** — data analysis and report creation

## Project files

```text
sql-sales-analysis-and-customer-insights/
├── Advanced Analysis.sql
├── README.md
├── fact_sales.csv
├── dim_customers.csv
└── dim_products.csv
```

The CSV files are the source data used to populate the database tables. For a larger or more polished repository, these can be moved into a `data/` folder and the SQL script into a `sql/` folder.

## Dataset overview

The project uses three related tables:

| File / table | Description | Example fields |
|---|---|---|
| `fact_sales.csv` / `fact_sales` | Transaction-level sales records | `order_number`, `product_key`, `customer_key`, `order_date`, `sales_amount`, `quantity`, `price` |
| `dim_products.csv` / `dim_products` | Product information | `product_key`, `product_name`, `category`, `subcategory`, `cost` |
| `dim_customers.csv` / `dim_customers` | Customer information | `customer_key`, `customer_number`, `first_name`, `last_name`, `country`, `birthdate` |

The SQL script expects the tables to be available in the database under the `dbo` schema. The data needs to be imported into SQL Server before the queries and views can be run.

## Analysis performed

### 1. Sales trends over time

- Summarises sales, distinct customers, and quantities by year and month.
- Uses date functions and grouped aggregations to examine changes over time.

### 2. Cumulative metrics

- Calculates running sales totals using a window function.
- Calculates a running average of product prices across the selected time periods.

### 3. Product performance

- Aggregates sales by product and year.
- Compares each year's sales with the product's average yearly sales.
- Uses `LAG()` to compare sales with the previous year.
- Labels results as above/below average and increase/decrease where applicable.

### 4. Product cost segmentation

- Groups products into cost ranges.
- Counts how many products fall within each range.

### 5. Customer segmentation

- Groups customers into VIP, Regular, and New segments using spending and purchasing-history rules.
- Counts customers in each segment.

### 6. Category contribution

- Calculates sales totals by product category.
- Shows each category's share of total sales as a percentage.

### 7. Customer and product reports

The script defines report views intended to consolidate useful measures, including sales, order counts, quantities, product/customer counts, recency, customer segment, product segment, and average sales measures.

## SQL concepts practised

- `SELECT`, `WHERE`, `GROUP BY`, and `ORDER BY`
- Joins between fact and dimension tables
- Common table expressions (CTEs)
- Aggregate functions such as `SUM()`, `AVG()`, and `COUNT()`
- Window functions such as `SUM() OVER()`, `AVG() OVER()`, and `LAG()`
- Conditional logic with `CASE`
- Date functions such as `DATETRUNC()`, `DATEDIFF()`, and `YEAR()`
- Creating views for reusable reporting queries

## How to run the project

1. Install or open Microsoft SQL Server and SQL Server Management Studio (SSMS).
2. Create or select a database for this project.
3. Import the three CSV files into SQL Server as tables named `fact_sales`, `dim_products`, and `dim_customers` under the `dbo` schema.
4. Open `Advanced Analysis.sql` in SSMS.
5. Make sure the query window is connected to the correct SQL Server instance and database. Add or update a `USE [YourDatabaseName];` statement at the beginning if needed.
6. Execute the analysis queries in sections and review the result grids.
7. Run the report-view definitions after confirming the source tables exist and the script is using the correct database.

**Note:** The script uses SQL Server-specific syntax, including `DATETRUNC()`, `FORMAT()`, and `GO`. It is intended for Microsoft SQL Server, not MySQL.

## Results and findings

This section can be completed after the queries have been run and checked. Add a few concise findings supported by the actual query output—for example, the strongest-performing category, sales trend over time, or distribution of customer segments. No numerical findings are included here until the results have been verified.

## Learning outcomes

Through this project, I practised using SQL to organise and analyse relational sales data, compare performance across time periods, segment customers and products, and prepare reusable reporting views. It also gave me hands-on practice with the SQL workflow in SSMS, from querying joined tables to structuring business-oriented analysis.

## Acknowledgement

This is a tutorial-based learning project. Credit for the original project walkthrough and teaching approach belongs to the tutorial creator. The repository is intended to demonstrate my practice and understanding of the SQL techniques used.
