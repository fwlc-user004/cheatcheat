# 🏆 Ultimate MATLAB Cheat Sheet

---

## 📌 1. Introduction to MATLAB

MATLAB (**Matrix Laboratory**) is a high-level programming language used for **numerical computing, data analysis, and visualization**.

### 🔹 Basic MATLAB Syntax
```matlab
% Print "Hello, MATLAB!"
disp('Hello, MATLAB!')
```

### 🔹 Running MATLAB Code
- Run individual commands in the **Command Window**.
- Save scripts as `.m` files and execute them using `run script_name`.

---

## 📌 2. Variables and Data Types

### 🔹 Declaring Variables
```matlab
x = 10;         % Integer
y = 3.14;       % Floating point
name = 'Alice'; % String
isActive = true; % Boolean
```

### 🔹 Checking Data Type
```matlab
class(x)  % Returns 'double'
```

### 🔹 Type Conversion
```matlab
num = str2double('42');  % Convert string to number
str = num2str(100);      % Convert number to string
```

---

## 📌 3. Vectors and Matrices

### 🔹 Creating Vectors
```matlab
v = [1, 2, 3, 4, 5];  % Row vector
v_col = [1; 2; 3];    % Column vector
```

### 🔹 Matrix Operations
```matlab
A = [1 2; 3 4];   % 2x2 Matrix
B = [5 6; 7 8];
C = A + B;        % Matrix addition
D = A * B;        % Matrix multiplication
E = A .* B;       % Element-wise multiplication
F = inv(A);       % Inverse of A
```

### 🔹 Accessing Elements
```matlab
A(1,2)  % First row, second column
A(:,1)  % First column
A(2,:)  % Second row
```

---

## 📌 4. Control Flow (Conditions & Loops)

### 🔹 If-Else Statement
```matlab
x = 10;
if x > 5
    disp('Greater than 5')
else
    disp('5 or less')
end
```

### 🔹 For Loop
```matlab
for i = 1:5
    disp(i)
end
```

### 🔹 While Loop
```matlab
i = 0;
while i < 5
    disp(i)
    i = i + 1;
end
```

---

## 📌 5. Functions

### 🔹 Defining Functions
```matlab
function result = addNumbers(a, b)
    result = a + b;
end
```

### 🔹 Calling a Function
```matlab
sum = addNumbers(5, 3);
disp(sum);
```

---

## 📌 6. Data Import and Export

### 🔹 Reading Data from a File
```matlab
data = readmatrix('data.csv');
```

### 🔹 Writing Data to a File
```matlab
writematrix(data, 'output.csv');
```

---

## 📌 7. Plotting and Visualization

### 🔹 Line Plot
```matlab
x = 0:0.1:10;
y = sin(x);
plot(x, y)
xlabel('X-axis')
ylabel('Y-axis')
title('Sine Wave')
grid on
```

### 🔹 Scatter Plot
```matlab
scatter(x, y)
```

### 🔹 Bar Plot
```matlab
bar([1 2 3 4 5], [5 3 8 6 7])
```

---

## 📌 8. Statistical Functions

### 🔹 Basic Statistics
```matlab
mean(data)  % Mean
median(data) % Median
std(data)  % Standard Deviation
```

### 🔹 Correlation
```matlab
corrcoef(data)
```

### 🔹 Linear Regression
```matlab
coefficients = polyfit(x, y, 1);
```

---

## 📌 9. Working with Images

### 🔹 Load and Display an Image
```matlab
img = imread('image.jpg');
imshow(img)
```

### 🔹 Convert Image to Grayscale
```matlab
grayImg = rgb2gray(img);
imshow(grayImg)
```

---

## 📌 10. Simulink (Graphical Modeling)

MATLAB integrates with **Simulink**, a graphical programming environment for modeling and simulating dynamic systems.

```matlab
simulink
```

---
