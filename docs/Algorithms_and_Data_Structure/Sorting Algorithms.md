# 🔢 Sorting Algorithms Cheatsheet

## 🔹 Introduction
Sorting algorithms are used to **rearrange elements** in a list or array in a specific order (ascending or descending). Choosing the right sorting algorithm depends on **time complexity, space complexity, and stability**.

---

## 🔹 Bubble Sort
### ✅ Definition:
A simple sorting algorithm that repeatedly **swaps adjacent elements** if they are in the wrong order.

### 📌 Implementation (Python):
```python
def bubble_sort(arr):
    n = len(arr)
    for i in range(n):
        swapped = False
        for j in range(0, n-i-1):
            if arr[j] > arr[j+1]:
                arr[j], arr[j+1] = arr[j+1], arr[j]
                swapped = True
        if not swapped:
            break
    return arr
```

### ⏳ Time Complexity:
| Case       | Complexity |
|------------|------------|
| Best Case  | O(n)       |
| Average Case | O(n²)    |
| Worst Case | O(n²)     |

---

## 🔹 Selection Sort
### ✅ Definition:
Finds the **smallest element** and swaps it with the first element, then repeats for the rest.

### 📌 Implementation:
```python
def selection_sort(arr):
    for i in range(len(arr)):
        min_idx = i
        for j in range(i+1, len(arr)):
            if arr[j] < arr[min_idx]:
                min_idx = j
        arr[i], arr[min_idx] = arr[min_idx], arr[i]
    return arr
```

### ⏳ Time Complexity:
| Case       | Complexity |
|------------|------------|
| Best Case  | O(n²)      |
| Average Case | O(n²)    |
| Worst Case | O(n²)     |

---

## 🔹 Insertion Sort
### ✅ Definition:
Iterates through the array, **shifting elements** to insert each element into its correct position.

### 📌 Implementation:
```python
def insertion_sort(arr):
    for i in range(1, len(arr)):
        key = arr[i]
        j = i-1
        while j >= 0 and arr[j] > key:
            arr[j+1] = arr[j]
            j -= 1
        arr[j+1] = key
    return arr
```

### ⏳ Time Complexity:
| Case       | Complexity |
|------------|------------|
| Best Case  | O(n)       |
| Average Case | O(n²)    |
| Worst Case | O(n²)     |

---

## 🔹 Merge Sort
### ✅ Definition:
A **divide-and-conquer** algorithm that splits an array into halves, sorts them recursively, and merges them back.

### 📌 Implementation:
```python
def merge_sort(arr):
    if len(arr) > 1:
        mid = len(arr) // 2
        left_half = arr[:mid]
        right_half = arr[mid:]

        merge_sort(left_half)
        merge_sort(right_half)

        i = j = k = 0
        while i < len(left_half) and j < len(right_half):
            if left_half[i] < right_half[j]:
                arr[k] = left_half[i]
                i += 1
            else:
                arr[k] = right_half[j]
                j += 1
            k += 1
        
        while i < len(left_half):
            arr[k] = left_half[i]
            i += 1
            k += 1
        
        while j < len(right_half):
            arr[k] = right_half[j]
            j += 1
            k += 1
    return arr
```

### ⏳ Time Complexity:
| Case       | Complexity |
|------------|------------|
| Best Case  | O(n log n) |
| Average Case | O(n log n) |
| Worst Case | O(n log n) |

---

## 🔹 Quick Sort
### ✅ Definition:
A **divide-and-conquer** algorithm that selects a **pivot**, partitions the array, and recursively sorts the partitions.

### 📌 Implementation:
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

### ⏳ Time Complexity:
| Case       | Complexity |
|------------|------------|
| Best Case  | O(n log n) |
| Average Case | O(n log n) |
| Worst Case | O(n²) |

---

## 🔹 Heap Sort
### ✅ Definition:
Uses a **binary heap** data structure to sort elements.

### 📌 Implementation:
```python
def heapify(arr, n, i):
    largest = i
    left = 2 * i + 1
    right = 2 * i + 2

    if left < n and arr[i] < arr[left]:
        largest = left
    if right < n and arr[largest] < arr[right]:
        largest = right
    if largest != i:
        arr[i], arr[largest] = arr[largest], arr[i]
        heapify(arr, n, largest)

def heap_sort(arr):
    n = len(arr)
    for i in range(n // 2 - 1, -1, -1):
        heapify(arr, n, i)
    for i in range(n - 1, 0, -1):
        arr[i], arr[0] = arr[0], arr[i]
        heapify(arr, i, 0)
    return arr
```

### ⏳ Time Complexity:
| Case       | Complexity |
|------------|------------|
| Best Case  | O(n log n) |
| Average Case | O(n log n) |
| Worst Case | O(n log n) |

---

## 🔹 Sorting Algorithm Comparison
| Algorithm      | Best Case | Average Case | Worst Case | Space Complexity |
|---------------|----------|--------------|------------|------------------|
| Bubble Sort   | O(n)     | O(n²)        | O(n²)      | O(1) |
| Selection Sort | O(n²)   | O(n²)        | O(n²)      | O(1) |
| Insertion Sort | O(n)    | O(n²)        | O(n²)      | O(1) |
| Merge Sort    | O(n log n) | O(n log n) | O(n log n) | O(n) |
| Quick Sort    | O(n log n) | O(n log n) | O(n²)      | O(log n) |
| Heap Sort     | O(n log n) | O(n log n) | O(n log n) | O(1) |

---

## 🔹 Sorting Best Practices
- Use **Quick Sort** for general-purpose sorting.
- Use **Merge Sort** for stable sorting.
- Use **Heap Sort** for efficient **priority queues**.
- Use **Insertion Sort** for small or nearly sorted lists.

---