# Northwinds-PostgresSQL

TASK: Practice writing SQL statements on the Northwind database.

SETUP:
● In pgAdmin, create a database called northwind.
● Open up a SQL window. Copy-paste and run this file...
https://raw.githubusercontent.com/pthom/northwind_psql/master/northwind.sql

DETAILS:
Write SQL queries to do the following tasks. Record these queries in a text document so you can repeat them in class.
1. Select all the records from the "Customers" table.
  SELECT * FROM customers;

2. Get distinct countries from the Customers table.
  SELECT DISTINCT country FROM customers;

3. Get all the records from the table Customers where the Customer’s ID starts with “BL”.
  SELECT * FROM customers WHERE customer_id SIMILAR TO ‘(BL)%’;

4. Get the first 100 records of the orders table.
  SELECT * FROM orders limit 100;

5. Get all customers that live in the postal codes 1010, 3012, 12209, and 05023.
  SELECT * FROM customers WHERE postal_code='1010' OR postal_code='3012' OR postal_code='12209' OR postal_code='05023';

6. Get all orders where the ShipRegion is not equal to NULL.
  SELECT * FROM orders WHERE ship_region IS NOT null;

7. Get all customers ordered by the country, then by the city.
  SELECT * FROM customers ORDER BY country, city;

8. Add a new customer to the customers table. You can use whatever values/
  INSERT INTO customers (customer_id, company_name, contact_name, contact_title, address, city, region, postal_code, country, phone, fax) 
  VALUES ('ID', 'Company', 'Contact', 'Title', 'Address', 'City', 'Region', 'Postal', 'Country', 'Phone', 'Fax');

9. Update all ShipRegion to the value ‘EuroZone’ in the Orders table, where the ShipCountry is equal to France.
  UPDATE orders SET ship_region='EuroZone' WHERE ship_country='France'; 

10. Delete all orders from `order_details` that have quantity of 1.
 	DELETE FROM order_details WHERE quantity=1;

11. Calculate the average, max, and min of the quantity at the `order details` table.
  SELECT AVG(quantity) AS "Average", MAX(quantity) AS "Maximum", MIN(quantity) AS "Minimum" FROM order_details;

12. Calculate the average, max, and min of the quantity at the `order details` table,
grouped by the orderid.
  SELECT AVG(quantity) AS "Average", MAX(quantity) AS "Maximum", MIN(quantity) AS "Minimum" FROM order_details GROUP BY order_id; 

13. Find the CustomerID that placed order 10290 (orders table)
  SELECT customer_id FROM orders WHERE order_id=10290;

BONUS:
14. Do an inner join, left join, right join on orders and customers tables. 
  SELECT * FROM orders INNER JOIN customers on orders.customer_id = customers.customer_id;
  SELECT * FROM customers LEFT JOIN orders on customers.customer_id=orders.customer_id;
  SELECT * FROM customers RIGHT JOIN orders on customers.customer_id=orders.customer_id;

15. Get employees’ firstname for all employees who report to no one. 
  SELECT first_name FROM employees WHERE reports_to IS null;

16. Get employees’ firstname for all employees who report to Andrew.
  SELECT first_name FROM employees WHERE reports_to=2;
