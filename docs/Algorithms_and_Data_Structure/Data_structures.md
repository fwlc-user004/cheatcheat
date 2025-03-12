# 🏷️ Data Structures Comprehensive Cheatsheet

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

### ⌛ Time Complexity:
| Operation | Average Case | Worst Case |
|-----------|------------|------------|
| Access    | O(1)       | O(1)       |
| Search    | O(n)       | O(n)       |
| Insert    | O(1)       | O(n)       |
| Delete    | O(n)       | O(n)       |

### ✅ Pros & Cons:
| Pros | Cons |
|------|------|
| Fast access by index (O(1)) | Insertion and deletion can be expensive (O(n)) |
| Memory-efficient | Fixed size (for static arrays) |

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

### ⌛ Time Complexity:
| Operation | Average Case | Worst Case |
|-----------|------------|------------|
| Access    | O(n)       | O(n)       |
| Search    | O(n)       | O(n)       |
| Insert    | O(1)       | O(1)       |
| Delete    | O(1)       | O(1)       |

### ✅ Pros & Cons:
| Pros | Cons |
|------|------|
| Dynamic size | Higher memory usage due to pointers |
| Fast insertion/deletion | Slower access time (O(n)) |

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

### ⌛ Time Complexity:
| Operation | Average Case | Worst Case |
|-----------|------------|------------|
| Insert    | O(1)       | O(n)       |
| Delete    | O(1)       | O(n)       |
| Search    | O(1)       | O(n)       |

### 📌 Collision Handling Techniques:
- **Chaining** → Store multiple values in the same bucket.
- **Open Addressing** → Find another available slot.

### ✅ Pros & Cons:
| Pros | Cons |
|------|------|
| Fast lookups (O(1) in average) | Not memory-efficient |
| Ideal for key-value mapping | Worst-case performance can be O(n) |

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

### ⌛ Time Complexity:
| Operation | Average Case | Worst Case |
|-----------|------------|------------|
| Insert    | O(log n)   | O(n)       |
| Search    | O(log n)   | O(n)       |
| Delete    | O(log n)   | O(n)       |

### ✅ Pros & Cons:
| Pros | Cons |
|------|------|
| Hierarchical structure | Tree balancing is complex |
| Used in databases and file systems | Insertion and deletion can be expensive |

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
from collections import defaultdict

graph = defaultdict(list)
graph['A'].append('B')
graph['A'].append('C')
graph['B'].append('A')
graph['B'].append('D')
```

### ⌛ Time Complexity:
| Operation | Adjacency List | Adjacency Matrix |
|-----------|---------------|-----------------|
| Add Edge  | O(1)          | O(1)            |
| Remove Edge | O(1)        | O(1)            |
| Search    | O(V + E)      | O(V²)           |

### ✅ Pros & Cons:
| Pros | Cons |
|------|------|
| Useful for modeling networks | More complex than trees |
| Efficient pathfinding algorithms (Dijkstra, A*) | Traversal can be costly |

---

## 🔹 Data Structures Best Practices
- **Choose the right data structure** for efficiency.
- **Use Hash Tables** for fast lookups.
- **Prefer Trees/Graphs** for hierarchical data.
- **Use Queues/Stacks** when order matters.

---

## 📄 Recommended Books:
- **"Data Structures and Algorithms in Python" by Michael T. Goodrich**
- **"Algorithms, Part I & II" by Robert Sedgewick**
- **"Introduction to Algorithms" by Cormen et al. (CLRS)**
