# 🏆 Ultimate R Programming Cheat Sheet

---

## 📌 1. Introduction to R

R is a **statistical computing and data visualization** language widely used in **data science, machine learning, and statistical analysis**.

### 🔹 Basic Structure of an R Script
```r
# Print Hello World
print("Hello, R!")
```

---

## 📌 2. Variables and Data Types

### 🔹 Assigning Variables
```r
x <- 10        # Integer
y <- 3.14      # Numeric (Float)
name <- "Alice" # Character (String)
is_active <- TRUE # Boolean (Logical)
```

### 🔹 Checking Data Type
```r
class(x)  # "numeric"
typeof(y) # "double"
```

### 🔹 Type Conversion
```r
num <- as.numeric("42")  # Convert string to numeric
str <- as.character(100) # Convert number to string
```

---

## 📌 3. Data Structures

### 🔹 Vectors (1D Array)
```r
numbers <- c(1, 2, 3, 4, 5)
numbers[1]   # Access first element
length(numbers) # Get vector length
```

### 🔹 Lists (Heterogeneous Data)
```r
my_list <- list("Alice", 25, TRUE)
my_list[[1]]  # Access first element
```

### 🔹 Matrices (2D Array)
```r
matrix_data <- matrix(1:9, nrow=3, ncol=3)
matrix_data[1,2]  # Access row 1, column 2
```

### 🔹 Data Frames (Like a Table)
```r
df <- data.frame(Name=c("Alice", "Bob"), Age=c(25, 30))
df$Name  # Access column
df[1,]   # Access first row
```

---

## 📌 4. Control Flow (Conditions & Loops)

### 🔹 If-Else Statement
```r
x <- 10
if (x > 5) {
    print("Greater than 5")
} else {
    print("5 or less")
}
```

### 🔹 For Loop
```r
for (i in 1:5) {
    print(i)
}
```

### 🔹 While Loop
```r
i <- 0
while (i < 5) {
    print(i)
    i <- i + 1
}
```

---

## 📌 5. Functions

### 🔹 Creating Functions
```r
add_numbers <- function(a, b) {
    return(a + b)
}
print(add_numbers(5, 3))
```

### 🔹 Anonymous Functions (Lambda)
```r
square <- function(x) x^2
print(square(4))
```

---

## 📌 6. Data Manipulation

### 🔹 Reading a CSV File
```r
df <- read.csv("data.csv")
head(df)  # View first rows
```

### 🔹 Filtering Data
```r
df[df$Age > 25, ]  # Select rows where Age > 25
```

### 🔹 Selecting Columns
```r
df$Name   # Select a column
df[, c("Name", "Age")]  # Select multiple columns
```

### 🔹 Sorting Data
```r
df <- df[order(df$Age), ]  # Sort by Age
```

---

## 📌 7. Plotting and Visualization

### 🔹 Basic Plot
```r
plot(df$Age, df$Name, main="Age vs Name", col="blue")
```

### 🔹 Histogram
```r
hist(df$Age, col="red", main="Age Distribution")
```

### 🔹 Boxplot
```r
boxplot(df$Age, main="Age Boxplot")
```

---

## 📌 8. Statistical Functions

### 🔹 Basic Statistics
```r
mean(df$Age)  # Mean
median(df$Age)  # Median
sd(df$Age)  # Standard Deviation
```

### 🔹 Correlation
```r
cor(df$Age, df$Salary)
```

### 🔹 Linear Regression
```r
model <- lm(Salary ~ Age, data=df)
summary(model)
```

---

## 📌 9. Packages and Libraries

### 🔹 Installing and Loading Packages
```r
install.packages("ggplot2")  # Install ggplot2
library(ggplot2)  # Load the package
```

---

## 📌 10. File Handling

### 🔹 Writing to a CSV File
```r
write.csv(df, "output.csv")
```

### 🔹 Reading a File
```r
data <- read.table("file.txt", header=TRUE, sep="	")
```

---
