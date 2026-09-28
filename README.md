# E-Commerce Sales Analytics Database (MySQL)

A normalized MySQL database for an online store, built to answer real business questions about revenue, customer behavior, and product performance using advanced SQL.

## Project Overview

This project models the data of an e-commerce business, from customers and products to orders, payments, and shipping. It then uses SQL to turn that raw data into decisions: which products drive revenue, which customers to retain, and how the business is growing month to month.

**Goals**
- Design a normalized (3NF) relational schema from scratch
- Load and clean a real-world dataset
- Use advanced SQL (joins, CTEs, window functions) for business analysis
- Apply database features: indexes, views, stored procedures, triggers, transactions

## Tech Stack

- **Database:** MySQL 8.x
- **Tools:** MySQL Workbench, dbdiagram.io (ER diagram)
- **Data:** [Olist Brazilian E-Commerce Dataset (Kaggle) / synthetic data via Python Faker]
- **Optional:** Power BI / Tableau / Python for visualization

## Database Schema

![ER Diagram](images/er_diagram.png)

| Table | Description |
|---|---|
| `customers` | Customer details and location |
| `categories` | Product categories |
| `products` | Product catalog with price and stock |
| `orders` | Order header: customer, date, status |
| `order_items` | Line items linking orders to products |
| `payments` | Payment method and amount per order |
| `shipping` | Shipping and delivery details |

**Design notes:** [Briefly explain key decisions, e.g. why `order_items` is separate from `orders`, foreign key rules, and how the schema reaches 3NF.]

## Repository Structure

```
├── schema/
│   └── create_tables.sql
├── data/
│   └── [sample CSVs or link to dataset]
├── queries/
│   ├── 01_basic_analysis.sql
│   ├── 02_window_functions.sql
│   ├── 03_rfm_segmentation.sql
│   └── 04_cohort_retention.sql
├── advanced/
│   ├── indexes.sql
│   ├── views.sql
│   ├── stored_procedures.sql
│   └── triggers.sql
├── images/
│   └── er_diagram.png
└── README.md
```

## How to Run

1. Clone the repository
```bash
   git clone https://github.com/[your-username]/[repo-name].git
```
2. Create the database and tables
```sql
   CREATE DATABASE ecommerce_db;
   USE ecommerce_db;
   SOURCE schema/create_tables.sql;
```
3. Import the data using `LOAD DATA INFILE` or the MySQL Workbench import wizard
4. Run the scripts in `queries/` in numbered order

## Business Questions Answered

| # | Question | SQL Concepts Used |
|---|---|---|
| 1 | What are the top 10 products by revenue? | JOIN, GROUP BY, ORDER BY |
| 2 | How does monthly revenue trend over time? | Date functions, aggregation |
| 3 | What is the running total of sales? | `SUM() OVER()` |
| 4 | Which products rank highest within each category? | `RANK()`, `ROW_NUMBER()` |
| 5 | What is the month-over-month revenue growth? | `LAG()`, CTEs |
| 6 | Who are one-time vs repeat customers? | Subqueries, CASE |
| 7 | How can customers be segmented by value? | RFM analysis with CTEs |
| 8 | What % of each signup cohort returns to buy again? | Cohort analysis |

## Key Insights

1. [e.g. Top 10% of customers generate X% of total revenue]
2. [e.g. Revenue peaks in month X, driven by category Y]
3. [e.g. Only X% of customers place a second order within 90 days]
4. [e.g. Category X has the highest revenue but the lowest repeat rate]
5. [e.g. Late deliveries correlate with lower repeat purchases]

## Advanced Database Features

- **Indexes:** Added an index on `[column]`, reducing query time from [X] to [Y]. `EXPLAIN` output is in `advanced/indexes.sql`.
- **Views:** `monthly_sales_summary` gives a ready-to-query monthly revenue report.
- **Stored procedure:** `place_order()` inserts an order, its items, and updates stock inside a transaction.
- **Trigger:** Logs an alert when product stock falls below [threshold].
- **Transactions:** `COMMIT` / `ROLLBACK` keep order placement consistent.

## Challenges and Learnings

- [Messy data issue you hit (nulls, duplicates, date formats) and how you fixed it]
- [A query you optimized and what you learned from `EXPLAIN`]
- [Something you broke on purpose to understand foreign keys]

## Future Improvements

- Build a Power BI / Tableau dashboard on top of the views
- Automate data loading with a Python script
- Add product reviews and a sentiment analysis table

## Author

**Nainika**
B.Tech, Electronics and Communication Engineering, SKIT Jaipur
[LinkedIn](https://linkedin.com/in/nainika-agrawal-007395289) · [GitHub](https://github.com/[your-username])
