# Sorting Algorithms Cheat Sheet

## 📌 Introduction
Sorting algorithms are fundamental in computer science for arranging data in a particular order (ascending or descending). Below is a concise guide to the most commonly used sorting algorithms.

---

## 🏷️ Classification of Sorting Algorithms

### 🔹 Comparison-based Sorting Algorithms:
- Quick Sort
- Heap Sort
- Merge Sort
- Insertion Sort
- Selection Sort
- Bubble Sort
- Tim Sort (Hybrid Sort)

### 🔹 Non-comparison-based Sorting Algorithms:
- Counting Sort (Works only with non-negative integers or bounded numeric values)
- Radix Sort (Works only with non-negative integers or bounded numeric values)

---

## 🚀 Common Sorting Algorithms

### 1️⃣ Tim Sort (Hybrid Sort: Merge Sort + Insertion Sort)
**Time Complexity:**
- Best: O(n)  
- Average: O(n log n)  
- Worst: O(n log n)  
- **Space Complexity:** O(n)  

**Description:**
Tim Sort is a hybrid sorting algorithm derived from Merge Sort and Insertion Sort. It divides the array into small segments (runs) and sorts them using Insertion Sort before merging them with Merge Sort.

**Use Case:**
- Used as the default sorting algorithm in Python and Java.
- Efficient for real-world data that often has runs of sorted elements.

**Advantages:**
- Adaptive: Performs well on partially sorted data.
- Stable sort.

```python
def tim_sort(arr):
    arr.sort()
    return arr
```

---

### 2️⃣ Quick Sort (Divide & Conquer)
**Time Complexity:**
- Best: O(n log n)  
- Average: O(n log n)  
- Worst: O(n²)  
- **Space Complexity:** O(log n) (In-place sorting)

**Description:**
Selects a pivot, partitions the array around the pivot, and recursively sorts the partitions.

**Use Case:**
- Ideal for general-purpose sorting.
- Often faster than Merge Sort for in-memory sorting.

**Disadvantages:**
- Worst-case performance is O(n²) when the pivot selection is poor.
- Not a stable sort.

```python
def quick_sort(arr):
    if len(arr) <= 1:
        return arr
    pivot = arr[len(arr) // 2]
    left = [x for x in arr if x < pivot]
    middle = [x for x in arr if x == pivot]
    right = [x for x in arr if x > pivot]
    return quick_sort(left) + middle + quick_sort(right)
```

---

## 🔹 Sorting Algorithm Stability
| Algorithm      | Stable?  |
|---------------|---------|
| Tim Sort      | ✅ Yes |
| Quick Sort    | ❌ No |
| Heap Sort     | ❌ No |
| Merge Sort    | ✅ Yes |
| Insertion Sort| ✅ Yes |
| Bubble Sort   | ✅ Yes |
| Selection Sort| ❌ No |
| Counting Sort | ✅ Yes |
| Radix Sort    | ✅ Yes |

---

## 📊 Sorting Algorithm Comparison
| Algorithm      | Best Case | Average Case | Worst Case | Space Complexity | Use Case |
|---------------|----------|--------------|------------|------------------|----------|
| Tim Sort      | O(n)     | O(n log n)   | O(n log n) | O(n)             | Default in Python & Java |
| Quick Sort    | O(n log n)| O(n log n)  | O(n²)      | O(log n)         | General Purpose Sorting |
| Heap Sort     | O(n log n)| O(n log n)  | O(n log n) | O(1)             | Priority Queues |
| Radix Sort    | O(nk)     | O(nk)       | O(nk)      | O(n + k)         | Large Integer Datasets (Only for non-negative integers) |
| Bubble Sort   | O(n)     | O(n²)        | O(n²)      | O(1)             | Small & Nearly Sorted Arrays (Adaptive) |
| Selection Sort| O(n²)    | O(n²)        | O(n²)      | O(1)             | Small Lists |
| Insertion Sort| O(n)     | O(n²)        | O(n²)      | O(1)             | Small & Nearly Sorted Arrays (Adaptive) |
| Merge Sort    | O(n log n)| O(n log n)  | O(n log n) | O(n)             | Stable Sorting & Linked Lists |
| Counting Sort | O(n + k) | O(n + k)    | O(n + k)   | O(k)             | Small Range Values (Only for non-negative integers) |

---

