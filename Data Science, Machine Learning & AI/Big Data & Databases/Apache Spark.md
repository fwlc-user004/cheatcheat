# ⚡ Apache Spark Comprehensive Cheatsheet

## 🔹 Introduction
Apache Spark is a **distributed computing framework** used for **big data processing, analytics, and machine learning**.

---

## 🔹 Installing Apache Spark
```sh
# Install Spark on Ubuntu
sudo apt update && sudo apt install -y openjdk-11-jdk
wget https://downloads.apache.org/spark/spark-3.3.0/spark-3.3.0-bin-hadoop3.tgz

# Extract & Set Environment Variables
tar -xvzf spark-3.3.0-bin-hadoop3.tgz
export SPARK_HOME="$HOME/spark-3.3.0-bin-hadoop3"
export PATH="$SPARK_HOME/bin:$PATH"
```

---

## 🔹 Starting Spark
```sh
# Start Spark shell
spark-shell

# Start PySpark (Python API)
pyspark
```

---

## 🔹 Creating a Spark Session
```python
from pyspark.sql import SparkSession

spark = SparkSession.builder \
    .appName("MyApp") \
    .getOrCreate()
```

---

## 🔹 Working with RDDs (Resilient Distributed Datasets)
### ✅ Creating an RDD
```python
rdd = spark.sparkContext.parallelize([("Alice", 30), ("Bob", 25)])
```

### ✅ RDD Transformations
```python
filtered_rdd = rdd.filter(lambda x: x[1] > 28)
```

### ✅ RDD Actions
```python
print(filtered_rdd.collect())  # Retrieve all elements
print(rdd.count())  # Count elements
```

---

## 🔹 Working with DataFrames
### ✅ Creating a DataFrame
```python
from pyspark.sql import Row

data = [Row(name="Alice", age=30), Row(name="Bob", age=25)]
df = spark.createDataFrame(data)
df.show()
```

### ✅ Reading a CSV File
```python
df = spark.read.csv("data.csv", header=True, inferSchema=True)
df.show()
```

### ✅ DataFrame Operations
```python
df.select("name").show()
df.filter(df.age > 28).show()
```

---

## 🔹 SQL Queries in Spark
```python
# Register DataFrame as SQL Table
df.createOrReplaceTempView("people")
sql_result = spark.sql("SELECT * FROM people WHERE age > 28")
sql_result.show()
```

---

## 🔹 Machine Learning with MLlib
### ✅ Linear Regression Example
```python
from pyspark.ml.regression import LinearRegression
from pyspark.ml.feature import VectorAssembler

data = [(1, 10), (2, 20), (3, 30)]
df = spark.createDataFrame(data, ["feature", "label"])

assembler = VectorAssembler(inputCols=["feature"], outputCol="features")
df = assembler.transform(df)

lr = LinearRegression(featuresCol="features", labelCol="label")
model = lr.fit(df)
print("Coefficients:", model.coefficients)
```

---

## 🔹 Best Practices
- **Use DataFrames instead of RDDs** for performance.
- **Partition data correctly** to optimize parallel processing.
- **Use caching (`df.cache()`)** to speed up iterative computations.
- **Tune Spark settings (`spark.conf.set()`)** for better performance.
- **Monitor jobs with Spark UI (`http://localhost:4040`)**.

---