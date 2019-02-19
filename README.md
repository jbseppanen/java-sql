# Introduction

Working with SQL

# Instructions

Surf to [SQL Try Editor at W3Schools.com](https://www.w3schools.com/Sql/tryit.asp?filename=trysql_select_top)  
Answer the following data queries. Keep track of the SQL you write by pasting it into this document under its appropriate header below. You will be submitting that through the regular fork, change, pull process.

### **Clicking the `Restore Database` button in the page will repopulate the database with the original data and discard all changes you have made**.

### 1.  find all customers that live in London. Returns 6 records.

### 2.  find all customers with postal code 1010. Returns 3 customers.

### 3.  find the phone number for the supplier with the id 11. Should be (010) 9984510.

### 4.  list orders descending by the order date. The order with date 1997-02-12 should be at the top.

### 5.  find all suppliers who have names longer than 20 characters. You can use `length(SupplierName)` to get the length of the name. Returns 11 records.

### 6.  find all customers that include the word "market" in the name. Should return 4 records.

### 7.  add a customer record for _"The Shire"_, the contact name is _"Bilbo Baggins"_ the address is _"1 Hobbit-Hole"_ in _"Bag End"_, postal code _"111"_ and the country is _"Middle Earth"_.

### 8.  update _Bilbo Baggins_ record so that the postal code changes to _"11122"_.

### 9.  list orders grouped by customer showing the number of orders per customer. _Rattlesnake Canyon Grocery_ should have 7 orders.

### 10. list customers names and the number of orders per customer. Sort the list by number of orders in descending order. _Ernst Handel_ should be at the top with 10 orders followed by _QUICK-Stop_, _Rattlesnake Canyon Grocery_ and _Wartian Herkku_ with 7 orders each.

### 11. list orders grouped by customer's city showing number of orders per city. Returns 58 Records with _Aachen_ showing 2 orders and _Albuquerque_ showing 7 orders.

### 12. delete all customers that have no orders. Should delete 17 (or 18 if you haven't deleted the record added) records.

## Create Database and Table

### Keep track of the code you write and paste at the end of this document

- use [`SQLite Studio`](https://sqlitestudio.pl/index.rvt) to create a database, name it `budget.sqlite3`.
- add an `accounts` table with the following _schema_:

  - `id`, numeric value with no decimal places that should autoincrement.
  - `name`, string, add whatever is necessary to make searching by name faster.
  - `budget` numeric value.

- constraints
  - the `id` should be the primary key for the table.
  - account `name` should be unique.
  - account `budget` is required.

Start of online W3Schools commands here:
________________________________________________________________________________________________________________________________

1.  SELECT * FROM Customers WHERE city = 'London';

2.  SELECT * FROM Customers WHERE postalcode = 1010

3.  SELECT phone FROM Suppliers WHERE supplierid = 11

4.  SELECT * FROM Orders ORDER BY orderdate DESC

5.  SELECT * FROM suppliers WHERE (SELECT length(SupplierName) > 20 FROM products)

6.  SELECT * FROM customers WHERE customername LIKE '%market%'

7.  INSERT INTO customers(customerid, customername, contactname, address, city, postalcode, country) VALUES (null, 'The Shire', 'Bilbo Baggins', '1 Hobbit-Hole', 'Bag End', 111, 'Middle Earth')

8.  UPDATE customers SET postalcode = 11122 WHERE contactname = 'Bilbo Baggins'

9.  SELECT customername, count(*) as 'Number of Orders' FROM orders LEFT JOIN customers ON orders.customerid = customers.customerid GROUP BY orders.customerid

10. SELECT customername, count(*) as Num_Of_Orders FROM orders LEFT JOIN customers ON orders.customerid = customers.customerid GROUP BY orders.customerid ORDER BY Num_Of_Orders DESC

11. SELECT city, count(*) as Num_Of_Orders FROM orders LEFT JOIN customers ON orders.customerid = customers.customerid GROUP BY customers.city ORDER BY city

12. DELETE FROM Customers WHERE CustomerID NOT IN (SELECT CustomerID FROM Orders)
