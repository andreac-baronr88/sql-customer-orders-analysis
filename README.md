# sql-customer-orders-analysis
SQL query to calculate total customers, total orders, and total spend per signup year.

Query Solution

SELECT 
    YEAR(c.signup_date) AS signup_year,
    COUNT(DISTINCT c.customer_id) AS total_customers,
    COUNT(o.order_id) AS total_orders, 
    SUM(o.total_amount) AS total_amount_spent
FROM customers c
JOIN orders o
    ON o.customer_id = c.customer_id
GROUP BY YEAR(c.signup_date)
ORDER BY signup_year;
