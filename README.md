🛒 Online Store Database Management & Reporting (SQL Project)
📌 Project Overview

This project demonstrates the design and implementation of a sample Online Store database using SQL.
It includes schema creation, sample data insertion, and SQL queries to generate meaningful business insights such as sales trends, top products, and customer purchase history.

🗂️ Project Structure
/Online-Store-SQL-Project
   ├── schema.sql   # Database schema (tables & relationships)
   ├── data.sql     # Sample dataset (INSERT statements)
   ├── queries.sql  # Reporting & analysis SQL queries
   └── README.md    # Project documentation

🏗️ Database Schema

The database contains the following tables:

Customers → Stores customer details (name, email, city, signup date).

Categories → Product categories (Electronics, Clothing, Books, etc.).

Products → Product catalog with price and category.

Orders → Order details (customer & date).

OrderItems → Line items for each order (product & quantity).

Entity-Relationship (ER) Example:

Customers ───< Orders ───< OrderItems >─── Products >─── Categories

📊 Sample Reports & Queries
1️⃣ Total Sales Revenue
SELECT SUM(p.price * oi.quantity) AS total_revenue
FROM OrderItems oi
JOIN Products p ON oi.product_id = p.product_id;

2️⃣ Top 3 Best-Selling Products
SELECT p.product_name, SUM(oi.quantity) AS total_sold
FROM OrderItems oi
JOIN Products p ON oi.product_id = p.product_id
GROUP BY p.product_name
ORDER BY total_sold DESC
LIMIT 3;

3️⃣ Customer Purchase History
SELECT c.name, o.order_id, o.order_date, p.product_name, oi.quantity
FROM Customers c
JOIN Orders o ON c.customer_id = o.customer_id
JOIN OrderItems oi ON o.order_id = oi.order_id
JOIN Products p ON oi.product_id = p.product_id
WHERE c.name = 'Alice Johnson';

4️⃣ Sales by Category
SELECT cat.category_name, SUM(p.price * oi.quantity) AS revenue
FROM OrderItems oi
JOIN Products p ON oi.product_id = p.product_id
JOIN Categories cat ON p.category_id = cat.category_id
GROUP BY cat.category_name;

5️⃣ Monthly Sales Trend
SELECT DATE_FORMAT(order_date, '%Y-%m') AS month, 
       SUM(p.price * oi.quantity) AS monthly_sales
FROM Orders o
JOIN OrderItems oi ON o.order_id = oi.order_id
JOIN Products p ON oi.product_id = p.product_id
GROUP BY month
ORDER BY month;

🚀 How to Run

Clone the repository:

git clone https://github.com/<your-username>/Online-Store-SQL-Project.git
cd Online-Store-SQL-Project


Import the schema:

SOURCE schema.sql;


Load sample data:

SOURCE data.sql;


Run reporting queries:

SOURCE queries.sql;

🛠️ Skills Highlighted

SQL (DDL, DML, Joins, Subqueries, Aggregate Functions)

Database Design (Relationships, Normalization)

Data Analysis & Reporting

📌 Future Enhancements

Add stored procedures & triggers for automation.

Create views for simplified reporting.

Connect with a Python/Power BI dashboard for visualization.
