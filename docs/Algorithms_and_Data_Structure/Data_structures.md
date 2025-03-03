layout: default

# 🏗️ Data Structures Comprehensive Cheatsheet

## 🔹 Introduction
Data structures are ways to **store and organize** data efficiently for different use cases. The choice of the right data structure can significantly affect the **performance** of an algorithm.

---

## 🔹 Arrays
### ✅ Definition:
A **fixed-size** or **dynamic** collection of elements stored in contiguous memory locations.

### 📌 Operations:
```python
arr = [1, 2, 3, 4, 5]  # Create an array
arr.append(6)  # Add element
arr.pop()  # Remove last element
print(arr[2])  # Access element by index
```

### ⏳ Time Complexity:
| Operation | Average Case | Worst Case |
|-----------|------------|------------|
| Access    | O(1)       | O(1)       |
| Search    | O(n)       | O(n)       |
| Insert    | O(1)       | O(n)       |
| Delete    | O(n)       | O(n)       |

---

## 🔹 Linked List
### ✅ Definition:
A data structure where **each element (node) contains a reference** to the next node in memory.

### 📌 Types:
- **Singly Linked List** → Each node points to the next.
- **Doubly Linked List** → Nodes have pointers to both next and previous.
- **Circular Linked List** → Last node points to the first node.

### 📌 Implementation (Python):
```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class LinkedList:
    def __init__(self):
        self.head = None
```

### ⏳ Time Complexity:
| Operation | Average Case | Worst Case |
|-----------|------------|------------|
| Access    | O(n)       | O(n)       |
| Search    | O(n)       | O(n)       |
| Insert    | O(1)       | O(1)       |
| Delete    | O(1)       | O(1)       |

---

## 🔹 Stacks (LIFO)
### ✅ Definition:
A **Last In First Out (LIFO)** data structure where elements are inserted and removed from the **same end**.

### 📌 Operations:
- **Push** (Insert an element)
- **Pop** (Remove the top element)
- **Peek** (View the top element without removing it)

### 📌 Implementation:
```python
stack = []
stack.append(1)  # Push
stack.append(2)
stack.pop()  # Pop
print(stack[-1])  # Peek
```

### ⏳ Time Complexity:
| Operation | Average Case | Worst Case |
|-----------|------------|------------|
| Push      | O(1)       | O(1)       |
| Pop       | O(1)       | O(1)       |
| Peek      | O(1)       | O(1)       |

---

## 🔹 Queues (FIFO)
### ✅ Definition:
A **First In First Out (FIFO)** data structure where elements are inserted at the **rear** and removed from the **front**.

### 📌 Types:
- **Simple Queue** → FIFO order.
- **Circular Queue** → The last position connects to the first.
- **Priority Queue** → Elements are dequeued based on priority.
- **Deque (Double-Ended Queue)** → Elements can be added/removed from both ends.

### 📌 Implementation:
```python
from collections import deque
queue = deque()
queue.append(1)  # Enqueue
queue.append(2)
queue.popleft()  # Dequeue
```

### ⏳ Time Complexity:
| Operation | Average Case | Worst Case |
|-----------|------------|------------|
| Enqueue   | O(1)       | O(1)       |
| Dequeue   | O(1)       | O(1)       |

---

## 🔹 Hash Tables (Dictionaries in Python)
### ✅ Definition:
A key-value storage where **keys are hashed** to find their associated values.

### 📌 Implementation:
```python
hash_table = {}
hash_table["name"] = "Alice"
print(hash_table["name"])  # Output: Alice
```

### ⏳ Time Complexity:
| Operation | Average Case | Worst Case |
|-----------|------------|------------|
| Insert    | O(1)       | O(n)       |
| Delete    | O(1)       | O(n)       |
| Search    | O(1)       | O(n)       |

---

## 🔹 Trees
### ✅ Definition:
A **hierarchical data structure** consisting of nodes where each node has a parent and children.

### 📌 Types:
- **Binary Tree** → Each node has at most 2 children.
- **Binary Search Tree (BST)** → Left child < Parent < Right child.
- **AVL Tree** → Self-balancing BST.
- **Heap** → Specialized tree-based structure.

### 📌 Implementation:
```python
class Node:
    def __init__(self, key):
        self.left = None
        self.right = None
        self.val = key
```

### ⏳ Time Complexity:
| Operation | Average Case | Worst Case |
|-----------|------------|------------|
| Insert    | O(log n)   | O(n)       |
| Search    | O(log n)   | O(n)       |
| Delete    | O(log n)   | O(n)       |

---

## 🔹 Graphs
### ✅ Definition:
A collection of **nodes (vertices)** connected by **edges**.

### 📌 Types:
- **Directed Graph (Digraph)** → Edges have direction.
- **Undirected Graph** → Edges have no direction.
- **Weighted Graph** → Edges have weights.

### 📌 Implementation:
```python
# Graph using adjacency list
graph = {
    'A': ['B', 'C'],
    'B': ['A', 'D'],
    'C': ['A', 'D'],
    'D': ['B', 'C']
}
```

### ⏳ Time Complexity:
| Operation | Adjacency List | Adjacency Matrix |
|-----------|---------------|-----------------|
| Add Edge  | O(1)          | O(1)            |
| Remove Edge | O(1)        | O(1)            |
| Search    | O(V + E)      | O(V²)           |

---

## 🔹 Data Structures Best Practices
- **Choose the right data structure** for efficiency.
- **Use Hash Tables** for fast lookups.
- **Prefer Trees/Graphs** for hierarchical data.
- **Use Queues/Stacks** when order matters.

---
