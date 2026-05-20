# E-Commerce SQL Retail Analysis

## Project Overview

This project is an SQL-based retail e-commerce data analysis project designed to generate business insights from customer orders, product categories, payments, reviews, and seller performance data. The objective of this project is to analyze transaction patterns, customer behavior, product performance, and operational efficiency using SQL queries.

The project simulates a real-world business analytics case where SQL is used to support decision-making for an e-commerce retail company.

## Business Problem

E-commerce companies handle large volumes of transaction data every day, but raw data alone does not directly provide useful business insights. The company needs to understand which products perform best, how customers behave, which payment methods are commonly used, how delivery performance affects customer satisfaction, and which sellers contribute most to revenue.

This project answers key business questions using SQL to help the business improve sales performance, customer experience, and operational decision-making.

## Objectives

- Analyze overall sales and order performance
- Identify top-performing product categories
- Understand customer purchasing behavior
- Analyze payment method usage
- Evaluate customer review scores
- Measure delivery and logistics performance
- Identify high-performing sellers
- Generate actionable business recommendations from SQL analysis

## Tools Used

- SQL Server
- SQL
- Relational Database
- E-Commerce Retail Dataset
- Data Cleaning
- Data Exploration
- Business Analysis

## Dataset Description

The dataset contains multiple tables related to e-commerce retail transactions. The data includes information about customers, orders, order items, products, payments, reviews, sellers, and product category translation.

Main tables used in this project:

```sql
olist_customers_dataset
olist_orders_dataset
olist_order_items_dataset
olist_products_dataset
olist_order_payments_dataset
olist_order_reviews_dataset
olist_sellers_dataset
product_category_name_translation
```

## Database Schema

The dataset follows a relational database structure where several tables are connected using unique keys such as `customer_id`, `order_id`, `product_id`, and `seller_id`.

Key relationships:

```text
customers → orders
orders → order_items
orders → payments
orders → reviews
order_items → products
order_items → sellers
products → product_category_translation
```

## Business Questions

1. What is the total number of orders and total revenue?
2. Which product categories generate the highest sales?
3. Which product categories have the highest and lowest review scores?
4. Which sellers generate the highest revenue?
5. What are the most commonly used payment methods?
6. How does delivery time affect customer review scores?
7. Which cities have the highest number of customers?
8. Which states generate the highest sales?
9. What is the monthly sales trend?
10. Which product categories have the highest number of orders?

## Sample SQL Query

Example query to analyze product categories with the highest and lowest average review scores:

```sql
SELECT 
    p.product_category_name AS product_category_portuguese,
    t.[English Name] AS product_category_english,
    ROUND(AVG(CAST(r.review_score AS FLOAT)), 2) AS average_review_score,
    COUNT(r.review_id) AS total_reviews
FROM dbo.olist_order_reviews_dataset r
JOIN dbo.olist_orders_dataset o
    ON r.order_id = o.order_id
JOIN dbo.olist_order_items_dataset oi
    ON o.order_id = oi.order_id
JOIN dbo.olist_products_dataset p
    ON oi.product_id = p.product_id
LEFT JOIN dbo.product_category_name_translation t
    ON p.product_category_name = t.[Portugese Name]
GROUP BY 
    p.product_category_name,
    t.[English Name]
ORDER BY average_review_score DESC;
```

## Key Analysis Areas

### 1. Sales Performance Analysis

This analysis identifies total sales, total orders, average order value, and monthly sales trends. It helps the business understand revenue growth and seasonal purchasing behavior.

### 2. Product Category Analysis

This analysis identifies which product categories generate the highest sales and which categories receive the best or worst customer reviews. This can help the company prioritize product assortment, promotion strategy, and inventory planning.

### 3. Customer Analysis

This analysis examines customer distribution by city and state to identify the strongest customer regions. The results can support targeted marketing campaigns and regional expansion strategy.

### 4. Seller Performance Analysis

This analysis identifies sellers with the highest contribution to sales. It helps the business understand which sellers are driving revenue and which sellers may need performance improvement.

### 5. Payment Analysis

This analysis evaluates the most frequently used payment methods by customers. It helps the business understand customer payment preferences and optimize payment experience.

### 6. Delivery Performance Analysis

This analysis measures delivery duration and evaluates how delivery time affects review scores. This helps identify whether late delivery has a negative impact on customer satisfaction.

## Expected Insights

- Product categories with high revenue potential
- Product categories with low customer satisfaction
- Top-performing sellers by revenue
- Customer concentration by city and state
- Monthly sales trend and seasonality
- Preferred payment methods among customers
- Relationship between delivery speed and review score

## Business Recommendations

Based on the SQL analysis, the business can make several strategic decisions:

- Increase marketing budget for high-performing product categories
- Improve product quality or seller standards for low-rated categories
- Strengthen partnerships with high-performing sellers
- Optimize delivery process to improve customer satisfaction
- Focus regional campaigns on cities and states with high customer activity
- Improve payment options based on customer preferences

## Project Outcome

This project demonstrates the ability to use SQL for business analytics and decision-making in an e-commerce retail environment. It shows how raw transactional data can be transformed into useful insights for sales, marketing, operations, and customer experience improvement.

## Skills Demonstrated

- SQL querying
- Data exploration
- Data cleaning
- Relational database analysis
- Aggregation and grouping
- Table joins
- Business problem solving
- Retail analytics
- Customer behavior analysis
- Sales performance analysis

## Future Improvements

- Build an interactive dashboard using Power BI, Tableau, or Looker Studio
- Add customer segmentation analysis
- Create seller performance scorecards
- Perform cohort analysis
- Add predictive analysis for sales forecasting
- Automate the SQL reporting process

## Author

**Cordirianto Alvian**  

## Dataset Access

Due to GitHub file size limitations, the full raw dataset is not uploaded directly to this repository.

The dataset used in this project is the Olist Brazilian E-Commerce Public Dataset, which can be accessed from Kaggle:

Dataset source: https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce

Only SQL scripts, analysis queries, schema documentation, and sample outputs are included in this repository.

