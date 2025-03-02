# 🔢 NumPy Cheatsheet

## 🔹 Introduction
NumPy (**Numerical Python**) is a **powerful library** for numerical computing in Python. It provides **multi-dimensional arrays**, **mathematical functions**, and **linear algebra tools**.

---

## 🔹 Installing NumPy
```sh
# Install NumPy using pip
pip install numpy

# Import NumPy
import numpy as np
```

---

## 🔹 Creating Arrays
### ✅ 1D, 2D, and 3D Arrays
```python
arr1 = np.array([1, 2, 3])  # 1D Array
arr2 = np.array([[1, 2, 3], [4, 5, 6]])  # 2D Array
arr3 = np.array([[[1, 2], [3, 4]], [[5, 6], [7, 8]]])  # 3D Array
```

### ✅ Special Arrays
```python
np.zeros((3,3))  # 3x3 matrix of zeros
np.ones((2,2))   # 2x2 matrix of ones
np.eye(4)        # Identity matrix (4x4)
np.full((2,3), 7) # 2x3 matrix filled with 7
```

### ✅ Random Arrays
```python
np.random.rand(3,3)    # Uniform random values (0 to 1)
np.random.randint(1, 10, (2, 3))  # Random integers
```

---

## 🔹 Array Properties
```python
arr.shape   # Get dimensions of array
arr.size    # Get total number of elements
arr.dtype   # Get data type
```

---

## 🔹 Indexing & Slicing
```python
arr = np.array([10, 20, 30, 40, 50])
print(arr[0])   # First element
print(arr[-1])  # Last element
print(arr[1:4]) # Slice elements
```

---

## 🔹 Reshaping Arrays
```python
arr.reshape(2, 3)  # Reshape 1D to 2D
arr.flatten()      # Flatten multi-dimensional array
```

---

## 🔹 Mathematical Operations
```python
arr1 + arr2  # Element-wise addition
arr1 - arr2  # Element-wise subtraction
arr1 * arr2  # Element-wise multiplication
arr1 / arr2  # Element-wise division
np.sqrt(arr)  # Square root
np.exp(arr)   # Exponential function
np.log(arr)   # Natural logarithm
```

---

## 🔹 Aggregate Functions
```python
np.sum(arr)  # Sum of elements
np.mean(arr) # Mean (average)
np.min(arr)  # Minimum value
np.max(arr)  # Maximum value
np.std(arr)  # Standard deviation
```

---

## 🔹 Linear Algebra
```python
np.dot(A, B)  # Matrix multiplication
np.linalg.inv(A)  # Inverse of matrix
np.linalg.det(A)  # Determinant of matrix
np.linalg.eig(A)  # Eigenvalues & eigenvectors
```

---

## 🔹 Saving & Loading Data
```python
np.save('array.npy', arr)  # Save array to file
arr = np.load('array.npy') # Load array from file
```

---

## 🔹 Best Practices
- **Use vectorized operations** instead of loops for performance.
- **Check array shapes** before performing matrix operations.
- **Use `.astype()`** to convert data types efficiently.
- **Utilize broadcasting** for arithmetic on different-sized arrays.

---