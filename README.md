# pizza-sales-SQL-project
knowing end to end pizza sales
# 🍕 Pizza Sales Analysis using SQL

![SQL](https://img.shields.io/badge/SQL-MySQL-blue)
![Data Analysis](https://img.shields.io/badge/Data%20Analysis-SQL-orange)
![Status](https://img.shields.io/badge/Project-Completed-success)

## 📌 Project Overview

This project performs an **end-to-end analysis of pizza sales data using SQL** to uncover meaningful business insights related to sales performance, customer ordering patterns, product popularity, revenue generation, and operational trends.

The objective is to transform raw transactional data into actionable insights that can help a pizza business understand its customers, identify high-performing products, optimize its menu, and improve sales performance.

---

## 🎯 Business Objectives

The analysis focuses on answering important business questions such as:

* How many orders were placed?
* What is the total revenue generated?
* What is the average order value?
* Which pizzas are the most popular?
* Which pizzas generate the highest revenue?
* Which pizza categories contribute the most to sales?
* What pizza sizes are ordered most frequently?
* What are the busiest ordering hours?
* Which days generate the highest number of orders?
* What percentage of revenue comes from each pizza category?
* What are the top-performing pizzas within each category?
* How does revenue change over time?

---

## 🗂️ Dataset

The project uses a relational pizza-sales dataset containing information about:

### 1. Orders

Contains order-level information.

| Column       | Description             |
| ------------ | ----------------------- |
| `order_id`   | Unique order identifier |
| `order_date` | Date of the order       |
| `order_time` | Time of the order       |

### 2. Order Details

Contains information about individual pizzas included in each order.

| Column             | Description                    |
| ------------------ | ------------------------------ |
| `order_details_id` | Unique order-detail identifier |
| `order_id`         | Related order ID               |
| `pizza_id`         | Pizza identifier               |
| `quantity`         | Number of pizzas ordered       |

### 3. Pizzas

Contains pricing and size information.

| Column          | Description             |
| --------------- | ----------------------- |
| `pizza_id`      | Unique pizza identifier |
| `pizza_type_id` | Pizza type identifier   |
| `size`          | Pizza size              |
| `price`         | Price of the pizza      |

### 4. Pizza Types

Contains information about pizza products.

| Column          | Description                  |
| --------------- | ---------------------------- |
| `pizza_type_id` | Unique pizza type identifier |
| `name`          | Pizza name                   |
| `category`      | Pizza category               |
| `ingredients`   | Ingredients used             |

---

## 🛠️ Tools & Technologies

* **MySQL**
* **SQL**
* Relational Database Analysis
* Data Aggregation
* Business Intelligence / Data Analytics

---

## 🧠 SQL Concepts Used

This project demonstrates practical SQL skills including:

* `SELECT`
* `WHERE`
* `GROUP BY`
* `ORDER BY`
* `HAVING`
* `DISTINCT`
* `COUNT()`
* `SUM()`
* `AVG()`
* `MIN()`
* `MAX()`
* `ROUND()`
* `CASE WHEN`
* `JOIN`
* Subqueries
* Common Table Expressions (CTEs)
* Window Functions
* Date and Time Functions
* Ranking
* Cumulative Revenue Analysis
* Percentage Contribution Analysis

---

## 🔗 Database Relationships

The project uses four related tables:

```text
                 ┌───────────────┐
                 │    Orders     │
                 │───────────────│
                 │ order_id      │
                 │ order_date    │
                 │ order_time    │
                 └───────┬───────┘
                         │
                         │ order_id
                         ▼
              ┌─────────────────────┐
              │   Order Details     │
              │─────────────────────│
              │ order_details_id    │
              │ order_id            │
              │ pizza_id            │
              │ quantity             │
              └──────────┬──────────┘
                         │
                         │ pizza_id
                         ▼
                 ┌───────────────┐
                 │    Pizzas     │
                 │───────────────│
                 │ pizza_id      │
                 │ pizza_type_id │
                 │ size          │
                 │ price         │
                 └───────┬───────┘
                         │
                         │ pizza_type_id
                         ▼
               ┌──────────────────┐
               │   Pizza Types    │
               │──────────────────│
               │ pizza_type_id    │
               │ name             │
               │ category         │
               │ ingredients      │
               └──────────────────┘
```

---

## 📊 Analysis Performed

### 🔹 Basic Analysis

The project calculates:

* Total number of orders
* Total pizzas sold
* Total revenue
* Average order value
* Average pizza price
* Minimum pizza price
* Maximum pizza price

### 🔹 Product Analysis

The analysis identifies:

* Most frequently ordered pizzas
* Least frequently ordered pizzas
* Highest-revenue pizzas
* Lowest-revenue pizzas
* Most popular pizza sizes
* Best-performing pizza categories

### 🔹 Time-Based Analysis

The project analyzes:

* Orders by day
* Orders by month
* Orders by hour
* Peak ordering periods
* Monthly revenue trends
* Daily revenue trends

### 🔹 Revenue Analysis

Revenue is calculated using:

```sql
Revenue = Pizza Price × Quantity
```

The project also analyzes:

* Revenue by pizza
* Revenue by category
* Revenue by size
* Percentage revenue contribution
* Cumulative revenue over time

### 🔹 Advanced Analysis

Advanced SQL techniques are used to answer questions such as:

* What are the top 3 pizzas by revenue within each category?
* What percentage of total revenue does each category contribute?
* How does cumulative revenue change over time?
* Which products perform best based on different sales metrics?

---

## 📈 Key Business Insights

The analysis can help a pizza business:

### Product Strategy

Identify high-performing and low-performing pizzas to understand customer preferences.

### Menu Optimization

Understand which pizza sizes and categories have stronger demand.

### Revenue Optimization

Identify products and categories that contribute significantly to overall revenue.

### Staffing Optimization

Use hourly and daily order patterns to understand peak periods and plan staffing accordingly.

### Marketing Strategy

Use sales performance to identify products that may benefit from promotions or targeted campaigns.

---

## 📁 Project Structure

```text
pizza-sales-SQL-project/
│
├── README.md
│
├── mysql project.pdf
│
└── SQL Queries
```

> The repository currently contains the project documentation PDF and README.

---

## 🚀 How to Run the Project

### Step 1: Install MySQL

Install MySQL Server and MySQL Workbench.

### Step 2: Create the Database

```sql
CREATE DATABASE pizza_sales;
USE pizza_sales;
```

### Step 3: Create the Tables

Create the four tables:

```text
orders
order_details
pizzas
pizza_types
```

### Step 4: Import the Dataset

Load the corresponding CSV files into the tables.

### Step 5: Run the SQL Queries

Execute the analysis queries in MySQL Workbench.

---

## 💡 Example SQL Analysis

### Total Revenue

```sql
SELECT 
    ROUND(SUM(p.price * od.quantity), 2) AS total_revenue
FROM order_details od
JOIN pizzas p
    ON od.pizza_id = p.pizza_id;
```

### Total Orders

```sql
SELECT 
    COUNT(DISTINCT order_id) AS total_orders
FROM orders;
```

### Top-Selling Pizzas

```sql
SELECT 
    pt.name,
    SUM(od.quantity) AS total_pizzas_sold
FROM order_details od
JOIN pizzas p
    ON od.pizza_id = p.pizza_id
JOIN pizza_types pt
    ON p.pizza_type_id = pt.pizza_type_id
GROUP BY pt.name
ORDER BY total_pizzas_sold DESC;
```

### Revenue by Pizza Category

```sql
SELECT 
    pt.category,
    ROUND(SUM(p.price * od.quantity), 2) AS revenue
FROM order_details od
JOIN pizzas p
    ON od.pizza_id = p.pizza_id
JOIN pizza_types pt
    ON p.pizza_type_id = pt.pizza_type_id
GROUP BY pt.category
ORDER BY revenue DESC;
```

---

## 📌 Skills Demonstrated

This project demonstrates practical skills relevant to **Data Analyst and Business Analyst roles**, including:

**SQL • MySQL • Data Cleaning • Data Exploration • Data Aggregation • Joins • CTEs • Subqueries • Window Functions • Business Analysis • KPI Analysis • Revenue Analysis • Trend Analysis • Data-Driven Decision Making**

---

## 👨‍💻 Author

**Prince Kumar**

Data Science / Data Analytics Enthusiast

* GitHub: [Prince13045](https://github.com/Prince13045)

---

## ⭐ Project

If you find this project useful, consider giving the repository a ⭐.

**Repository:**
https://github.com/Prince13045/pizza-sales-SQL-project
