# 🗄️ SQL & NoSQL for Big Data Cheatsheet

## 🔹 Introduction
Big Data systems use **SQL (Structured Query Language) databases** for structured data and **NoSQL (Not Only SQL) databases** for flexible, high-volume data.

---

## 🔹 SQL for Big Data
### ✅ Popular SQL Databases for Big Data
- **Apache Hive** → SQL-like querying on Hadoop.
- **Google BigQuery** → Scalable, serverless SQL database.
- **Amazon Redshift** → Cloud-based data warehousing.
- **PostgreSQL** → Advanced relational database with extensions for Big Data.

### 📌 Common SQL Queries for Big Data
```sql
-- Select top 100 records from a big dataset
SELECT * FROM big_data_table LIMIT 100;

-- Aggregate data by category
SELECT category, COUNT(*) FROM transactions GROUP BY category;

-- Optimize query using indexes
CREATE INDEX idx_category ON transactions (category);
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

---

## 🔹 NoSQL for Big Data
### ✅ Types of NoSQL Databases
| Type          | Description & Example |
|--------------|-----------------------|
| **Key-Value**  | Fast lookups, caching (Redis, Amazon DynamoDB) |
| **Document**   | JSON-based storage (MongoDB, CouchDB) |
| **Columnar**   | Optimized for analytics (Apache Cassandra, Google Bigtable) |
| **Graph**      | Relationship-based queries (Neo4j, Amazon Neptune) |

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

---

## 🔹 SQL vs NoSQL for Big Data
| Feature        | SQL Databases | NoSQL Databases |
|--------------|--------------|----------------|
| **Structure** | Fixed schema (tables) | Flexible schema (documents, key-value) |
| **Scalability** | Vertical scaling | Horizontal scaling (distributed) |
| **Use Case** | Structured data, OLAP | Unstructured, high-velocity data |
| **Examples** | MySQL, PostgreSQL, BigQuery | MongoDB, Cassandra, DynamoDB |

---

## 🔹 Best Practices for Big Data
- **Use partitioning & indexing** for faster SQL queries.
- **Choose NoSQL for high-velocity, unstructured data.**
- **Optimize queries** with distributed databases (e.g., BigQuery, Redshift).
- **Use caching** (Redis, Memcached) for real-time analytics.
- **Implement data replication** for high availability.

---