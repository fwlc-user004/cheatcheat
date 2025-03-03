# 🗄️ SQL (MySQL, PostgreSQL, SQLite) Comprehensive Cheatsheet

## 🔹 Basic SQL Syntax
```sql
SELECT column1, column2 FROM table_name;
INSERT INTO table_name (column1, column2) VALUES ('value1', 'value2');
UPDATE table_name SET column1 = 'new_value' WHERE condition;
DELETE FROM table_name WHERE condition;
```

---

## 🔹 Database Creation & Management
```sql
-- Create a database
CREATE DATABASE my_database;

-- Select a database
USE my_database; -- MySQL only
\c my_database; -- PostgreSQL only

-- Drop a database
DROP DATABASE my_database;
```

---

## 🔹 Table Operations
```sql
-- Create a table
CREATE TABLE users (
    id SERIAL PRIMARY KEY, -- AUTO_INCREMENT in MySQL
    name VARCHAR(100) NOT NULL,
    email VARCHAR(150) UNIQUE NOT NULL,
    age INT CHECK (age >= 18)
);

-- Drop a table
DROP TABLE users;
```

---

## 🔹 Data Types
```sql
-- Common Data Types
INT, BIGINT, FLOAT, DECIMAL(10,2)
VARCHAR(255), TEXT
DATE, TIMESTAMP, TIME
BOOLEAN
JSON (PostgreSQL, MySQL 5.7+)
```

---

## 🔹 Inserting & Selecting Data
```sql
-- Insert a record
INSERT INTO users (name, email, age) VALUES ('Alice', 'alice@example.com', 25);

-- Select all records
SELECT * FROM users;

-- Select with filtering
SELECT name, age FROM users WHERE age >= 21;

-- Select unique values
SELECT DISTINCT age FROM users;
```

---

## 🔹 Updating & Deleting Data
```sql
-- Update a record
UPDATE users SET email = 'new_email@example.com' WHERE id = 1;

-- Delete a record
DELETE FROM users WHERE id = 1;
```

---

## 🔹 Constraints & Keys
```sql
-- Adding a primary key
ALTER TABLE users ADD PRIMARY KEY (id);

-- Foreign Key Constraint
ALTER TABLE orders ADD CONSTRAINT fk_user FOREIGN KEY (user_id) REFERENCES users(id);
```

---

## 🔹 Joins
```sql
-- Inner Join
SELECT users.name, orders.order_date 
FROM users 
INNER JOIN orders ON users.id = orders.user_id;

-- Left Join
SELECT users.name, orders.order_date 
FROM users 
LEFT JOIN orders ON users.id = orders.user_id;

-- Right Join
SELECT users.name, orders.order_date 
FROM users 
RIGHT JOIN orders ON users.id = orders.user_id;
```

---

## 🔹 Aggregation & Grouping
```sql
-- Count number of users
SELECT COUNT(*) FROM users;

-- Average age of users
SELECT AVG(age) FROM users;

-- Group by age
SELECT age, COUNT(*) FROM users GROUP BY age;
```

---

## 🔹 Indexing for Performance
```sql
-- Create an index
CREATE INDEX idx_users_email ON users(email);

-- Drop an index
DROP INDEX idx_users_email;
```

---

## 🔹 Transactions
```sql
BEGIN TRANSACTION;
UPDATE accounts SET balance = balance - 100 WHERE id = 1;
UPDATE accounts SET balance = balance + 100 WHERE id = 2;
COMMIT; -- Use ROLLBACK if something goes wrong
```

---

## 🔹 Views
```sql
-- Create a view
CREATE VIEW user_orders AS
SELECT users.name, orders.order_date
FROM users
JOIN orders ON users.id = orders.user_id;

-- Use the view
SELECT * FROM user_orders;
```

---

## 🔹 Stored Procedures (MySQL & PostgreSQL)
```sql
-- Create a stored procedure
DELIMITER //
CREATE PROCEDURE GetUserById(IN user_id INT)
BEGIN
    SELECT * FROM users WHERE id = user_id;
END //
DELIMITER ;

-- Call a stored procedure
CALL GetUserById(1);
```

---

## 🔹 Common SQL Commands for SQLite
```sql
-- List all tables
.tables

-- Show table schema
.schema users

-- Enable foreign keys
PRAGMA foreign_keys = ON;
```

---

## 🔹 SQL Best Practices
- Always use **prepared statements** to prevent SQL injection.
- Use **proper indexing** to optimize query performance.
- Use **transactions** for atomic operations.
- Normalize database tables to **reduce redundancy**.
- Avoid using `SELECT *` in production queries.

---