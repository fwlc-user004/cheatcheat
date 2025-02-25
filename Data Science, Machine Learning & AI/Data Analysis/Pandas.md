# 🐼 Pandas Comprehensive Cheatsheet

## 🔹 Introduction
Pandas is a powerful **Python library for data manipulation and analysis**. It provides flexible **DataFrames** and **Series** structures for handling structured data.

---

## 🔹 Installing Pandas
```sh
# Install Pandas using pip
pip install pandas

# Import Pandas
import pandas as pd
```

---

## 🔹 Creating DataFrames
### ✅ From a Dictionary
```python
data = {'Name': ['Alice', 'Bob'], 'Age': [25, 30]}
df = pd.DataFrame(data)
print(df)
```

### ✅ From a CSV File
```python
df = pd.read_csv('data.csv')
```

### ✅ From an Excel File
```python
df = pd.read_excel('data.xlsx')
```

---

## 🔹 Viewing Data
```python
# Display first 5 rows
df.head()

# Display last 5 rows
df.tail()

# Display DataFrame summary
df.info()

# Display basic statistics
df.describe()
```

---

## 🔹 Selecting Data
```python
# Select a single column
df['Name']

# Select multiple columns
df[['Name', 'Age']]

# Select rows by index
df.iloc[0]   # First row
df.loc[0]    # First row (by label)
```

---

## 🔹 Filtering Data
```python
# Filter rows based on condition
df[df['Age'] > 25]

# Multiple conditions
df[(df['Age'] > 25) & (df['Name'] == 'Alice')]
```

---

## 🔹 Sorting Data
```python
# Sort by column
df.sort_values('Age', ascending=False)
```

---

## 🔹 Handling Missing Data
```python
# Check for missing values
df.isnull().sum()

# Fill missing values
df.fillna('Unknown')

# Drop rows with missing values
df.dropna()
```

---

## 🔹 Grouping & Aggregation
```python
# Group by column
df.groupby('Name').mean()
```

---

## 🔹 Merging & Joining DataFrames
```python
# Merge two DataFrames on a column
pd.merge(df1, df2, on='ID')

# Concatenate DataFrames vertically
pd.concat([df1, df2])
```

---

## 🔹 Exporting Data
```python
# Save DataFrame to CSV
df.to_csv('output.csv', index=False)

# Save DataFrame to Excel
df.to_excel('output.xlsx', index=False)
```

---

## 🔹 Best Practices
- **Use `.head()` to preview data** before processing.
- **Handle missing data early** to avoid errors.
- **Vectorize operations** instead of loops for better performance.
- **Use `.groupby()` for efficient data aggregation.**
- **Save large DataFrames in Parquet format** for faster I/O.

---