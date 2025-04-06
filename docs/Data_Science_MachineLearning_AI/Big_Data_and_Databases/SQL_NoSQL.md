
# 🗄️ SQL & NoSQL for Big Data Cheatsheet (Pro Edition)

## 🔹 Introduction
Big Data systems use **SQL databases** for structured, relational data, and **NoSQL databases** for scalable, semi-structured or unstructured data in high volume and variety.

---

## 🔹 SQL for Big Data

### ✅ Popular SQL Databases for Big Data
- **Apache Hive** → SQL-like querying on Hadoop.
- **Google BigQuery** → Scalable, serverless SQL database.
- **Amazon Redshift** → Cloud-based data warehousing.
- **PostgreSQL** → Advanced relational database with extensions for Big Data.
- **Snowflake** → Cloud-native data warehouse with automatic scaling and performance optimization.

### 📌 Common SQL Queries for Big Data
```sql
-- Select top 100 records from a big dataset
SELECT * FROM big_data_table LIMIT 100;

-- Aggregate data by category
SELECT category, COUNT(*) FROM transactions GROUP BY category;

-- Optimize query using indexes
CREATE INDEX idx_category ON transactions (category);

-- Join two big datasets
SELECT a.user_id, a.amount, b.region
FROM transactions a
JOIN users b ON a.user_id = b.user_id;

-- Use window function to rank transactions
SELECT user_id, amount,
       RANK() OVER (PARTITION BY user_id ORDER BY amount DESC) as rank
FROM transactions;
```

### 📌 Partitioning & Sharding
```sql
-- Partition table by date range
CREATE TABLE transactions (
    id INT,
    amount DECIMAL(10,2),
    transaction_date DATE
) PARTITION BY RANGE(transaction_date);
```

- **Partitioning** → Split data within the same database based on column values (e.g., date).
- **Sharding** → Distribute data across multiple machines or databases for scalability.

---

## 🔹 NoSQL for Big Data

### ✅ Types of NoSQL Databases

- **Key-Value:** Best for caching and fast lookups (e.g., Redis, DynamoDB)
- **Document:** Stores data as JSON-like documents (e.g., MongoDB, CouchDB)
- **Columnar:** Designed for high write throughput and analytics (e.g., Cassandra, Bigtable)
- **Graph:** Excellent for relationships and traversals (e.g., Neo4j, Amazon Neptune)

### 📌 MongoDB (Document-Based NoSQL)
```json
{
    "user_id": 123,
    "name": "Alice",
    "transactions": [
        {"date": "2024-01-01", "amount": 100},
        {"date": "2024-02-01", "amount": 200}
    ]
}
```
```sh
# Query MongoDB for a user
db.users.find({"user_id": 123})
```

**Aggregate Example:**
```js
db.transactions.aggregate([
  { $match: { user_id: 123 } },
  { $group: { _id: "$user_id", total: { $sum: "$amount" } } }
])
```

### 📌 Cassandra (Columnar NoSQL)
```sql
-- Create a table with wide columns
CREATE TABLE transactions (
    id UUID PRIMARY KEY,
    user_id INT,
    amount DECIMAL,
    transaction_date TIMESTAMP
) WITH CLUSTERING ORDER BY (transaction_date DESC);
```

- Cassandra is ideal for IoT or time-series data where fast writes and scalable reads are critical.

---

## 🔹 SQL vs NoSQL for Big Data

| Feature        | SQL Databases | NoSQL Databases |
|----------------|---------------|-----------------|
| **Structure**  | Fixed schema (tables) | Flexible schema (documents, key-value) |
| **Scalability**| Vertical scaling       | Horizontal scaling (distributed)       |
| **Use Case**   | Structured data, OLAP | Unstructured, high-velocity data       |
| **Examples**   | MySQL, PostgreSQL, BigQuery | MongoDB, Cassandra, DynamoDB     |
| **Consistency**| Strong consistency    | Eventual consistency                   |
| **Availability**| Medium (depends on setup) | High (designed for high availability) |

---

## 🔹 Best Practices for Big Data
- **Use partitioning & indexing** for faster SQL queries.
- **Choose NoSQL for high-velocity, unstructured data.**
- **Optimize queries** with distributed databases (e.g., BigQuery, Redshift).
- **Use caching** (Redis, Memcached) for real-time analytics.
- **Implement data replication** for high availability.
- **Use data lake architecture** when combining structured and unstructured data.
- **Monitor query performance** with tools like **EXPLAIN**, **Query Profiler**, or **Cloud Monitoring**.
- **Apply schema-on-read** approach in data lakes (e.g., Apache Hive, Athena).

---
