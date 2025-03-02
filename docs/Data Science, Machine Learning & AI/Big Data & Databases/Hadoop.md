# 🗄️ Hadoop Cheatsheet

## 🔹 Introduction
Apache Hadoop is a **distributed storage and processing framework** for **Big Data**. It provides scalable and fault-tolerant data storage and processing through **HDFS (Hadoop Distributed File System)** and **MapReduce**.

---

## 🔹 Installing Hadoop
```sh
# Install Hadoop on Ubuntu
sudo apt update && sudo apt install hadoop -y

# Check Hadoop version
hadoop version
```

---

## 🔹 Hadoop Ecosystem Components
| Component | Description |
|-----------|-------------|
| **HDFS** | Distributed storage system |
| **MapReduce** | Parallel data processing framework |
| **YARN** | Resource manager for Hadoop cluster |
| **Hive** | SQL-based query engine |
| **HBase** | NoSQL database on Hadoop |
| **Spark** | Fast in-memory processing engine |

---

## 🔹 HDFS Commands
### ✅ Checking HDFS Status
```sh
hdfs dfsadmin -report
```

### ✅ Create & List Directories
```sh
hdfs dfs -mkdir /bigdata
hdfs dfs -ls /
```

### ✅ Upload & Download Files
```sh
hdfs dfs -put localfile.txt /bigdata/
hdfs dfs -get /bigdata/localfile.txt local_copy.txt
```

### ✅ Delete Files
```sh
hdfs dfs -rm /bigdata/localfile.txt
```

---

## 🔹 Running a MapReduce Job
```sh
hadoop jar /usr/local/hadoop/share/hadoop/mapreduce/hadoop-mapreduce-examples-*.jar wordcount /input /output
```

### ✅ Check Job Status
```sh
yarn application -list
yarn logs -applicationId <application_id>
```

---

## 🔹 Hive (SQL on Hadoop)
### ✅ Start Hive CLI
```sh
hive
```

### ✅ Create a Table
```sql
CREATE TABLE users (
  id INT,
  name STRING,
  age INT
) ROW FORMAT DELIMITED
FIELDS TERMINATED BY ','
STORED AS TEXTFILE;
```

### ✅ Query Data
```sql
SELECT name, age FROM users WHERE age > 30;
```

---

## 🔹 Hadoop Configuration Files
| File | Purpose |
|------|---------|
| `core-site.xml` | Hadoop core settings (e.g., default filesystem) |
| `hdfs-site.xml` | HDFS configuration (replication, storage settings) |
| `yarn-site.xml` | YARN resource manager settings |
| `mapred-site.xml` | MapReduce job settings |

---

## 🔹 Best Practices
- **Use HDFS replication** for fault tolerance.
- **Optimize MapReduce jobs** with proper partitioning and combiner usage.
- **Monitor cluster health** using **YARN Resource Manager**.
- **Use Hive for SQL-like queries** instead of raw MapReduce.
- **Leverage Spark on Hadoop** for faster in-memory data processing.

---