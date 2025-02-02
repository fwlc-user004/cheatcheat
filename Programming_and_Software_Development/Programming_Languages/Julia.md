# 🏆 Ultimate Julia Cheat Sheet

---

## 📌 1. Introduction to Julia

**Julia** is a high-level, high-performance programming language designed for **numerical computing, data science, and machine learning**.

### 🔹 Running Julia Code
```julia
println("Hello, Julia!")
```

### 🔹 Installing and Running Julia
- Download and install Julia from [julialang.org](https://julialang.org/).
- Run Julia in the **REPL (Read-Eval-Print Loop)**.

---

## 📌 2. Variables and Data Types

### 🔹 Declaring Variables
```julia
x = 10         # Integer
y = 3.14       # Floating point
name = "Alice" # String
is_active = true # Boolean
```

### 🔹 Checking Data Type
```julia
typeof(x)  # Returns Int64
```

### 🔹 Type Conversion
```julia
num = parse(Int, "42")  # Convert string to integer
str = string(100)       # Convert number to string
```

---

## 📌 3. Data Structures

### 🔹 Arrays (1D, 2D, Multi-dimensional)
```julia
arr = [1, 2, 3, 4, 5]  # 1D array
arr[1]   # Access first element

matrix = [1 2 3; 4 5 6]  # 2D matrix
matrix[1,2]  # Access row 1, column 2
```

### 🔹 Tuples (Immutable Lists)
```julia
t = (1, "Alice", true)
t[2]  # Access second element
```

### 🔹 Dictionaries (Key-Value Pairs)
```julia
d = Dict("name" => "Alice", "age" => 25)
d["name"]  # Access value by key
```

---

## 📌 4. Control Flow (Conditions & Loops)

### 🔹 If-Else Statement
```julia
x = 10
if x > 5
    println("Greater than 5")
else
    println("5 or less")
end
```

### 🔹 For Loop
```julia
for i in 1:5
    println(i)
end
```

### 🔹 While Loop
```julia
i = 0
while i < 5
    println(i)
    i += 1
end
```

---

## 📌 5. Functions

### 🔹 Defining Functions
```julia
function add_numbers(a, b)
    return a + b
end

println(add_numbers(5, 3))
```

### 🔹 One-Line Functions (Lambda)
```julia
square(x) = x^2
println(square(4))
```

---

## 📌 6. Data Manipulation

### 🔹 Reading a CSV File
```julia
using CSV, DataFrames
df = CSV.read("data.csv", DataFrame)
```

### 🔹 Filtering Data
```julia
filtered_df = df[df.Age .> 25, :]
```

### 🔹 Selecting Columns
```julia
df.Name   # Select a column
df[:, [:Name, :Age]]  # Select multiple columns
```

### 🔹 Sorting Data
```julia
sort!(df, :Age)
```

---

## 📌 7. Plotting and Visualization

### 🔹 Using Plots Package
```julia
using Plots
x = 0:0.1:10
y = sin.(x)
plot(x, y, label="Sine Wave")
```

### 🔹 Histogram
```julia
histogram(df.Age, bins=10, title="Age Distribution")
```

### 🔹 Scatter Plot
```julia
scatter(df.Age, df.Salary, title="Age vs Salary")
```

---

## 📌 8. Statistical Functions

### 🔹 Basic Statistics
```julia
mean(df.Age)  # Mean
median(df.Age) # Median
std(df.Age)  # Standard Deviation
```

### 🔹 Correlation
```julia
cor(df.Age, df.Salary)
```

### 🔹 Linear Regression
```julia
using GLM
model = lm(@formula(Salary ~ Age), df)
```

---

## 📌 9. File Handling

### 🔹 Writing to a CSV File
```julia
CSV.write("output.csv", df)
```

### 🔹 Reading from a File
```julia
data = readlines("file.txt")
```

---

## 📌 10. Parallel Computing

### 🔹 Running Code in Parallel
```julia
using Distributed
addprocs(4)  # Add 4 worker processes

@distributed for i in 1:100
    println(i)
end
```

---
