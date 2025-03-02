# ✅ Assertion Cheat Sheet

## 🛠 What is an Assertion?
An **assertion** is a statement used in programming to check if a given condition is `True`. If the condition is `False`, an assertion error is raised.

### 🎯 Why Use Assertions?
✅ Helps in debugging by catching unexpected conditions  
✅ Improves code quality by enforcing invariants  
✅ Detects logical errors early in development  
✅ Can be disabled in production for performance optimization  

---

## 🚦 Common Assertion Usage in Different Languages

### 🟢 Python
```python
assert condition, "Error message (optional)"
```
**Example:**
```python
x = 10
assert x > 0, "x must be positive"
```
🔹 If `x > 0`, the program continues.  
🔹 If `x <= 0`, an `AssertionError` is raised.  

### 🔵 Java (JUnit)
```java
import static org.junit.jupiter.api.Assertions.*;
assertEquals(expected, actual);
assertTrue(condition);
assertFalse(condition);
```
**Example:**
```java
assertTrue(5 > 2, "5 should be greater than 2");
```

### 🟡 JavaScript (Node.js - Chai, Jest)
```javascript
const assert = require('assert');
assert.strictEqual(actual, expected, "Error message (optional)");
```
**Example:**
```javascript
assert.strictEqual(5 + 5, 10, "Math is broken!");
```

### 🔴 C++ (C++11)
```cpp
#include <cassert>
assert(expression);
```
**Example:**
```cpp
int x = 10;
assert(x > 0); // Passes
assert(x < 0); // Fails and terminates the program
```

### ⚫ C# (NUnit / Debug.Assert)
```csharp
using System.Diagnostics;
Debug.Assert(condition, "Error message (optional)");
```
**Example:**
```csharp
Debug.Assert(5 > 3, "5 should be greater than 3");
```

### 🟠 PHP (Assertions)
```php
assert($condition, "Error message (optional)");
```
**Example:**
```php
assert(5 > 3, "5 should be greater than 3");
```

---

## 🔥 Assertion Frameworks & Tools

| Language | Assertion Frameworks |
|----------|----------------------|
| **Python** | `unittest`, `pytest`, `doctest` |
| **Java** | `JUnit`, `TestNG` |
| **JavaScript** | `Chai`, `Jest`, `Mocha` |
| **C++** | `Google Test`, `Catch2` |
| **C#** | `NUnit`, `MSTest`, `xUnit` |
| **PHP** | `PHPUnit` |

---

## 📌 Best Practices for Assertions

✅ Use assertions **only in development and testing**  
✅ Provide **clear error messages** for failed assertions  
✅ **Do not use assertions for user input validation** (use exceptions instead)  
✅ Use assertions to **check invariants** in your program  
✅ Avoid side effects in assertion expressions  
✅ Use assertion libraries for better debugging and testing  

---

## ⚠️ Common Mistakes with Assertions

❌ Using assertions for handling expected failures (use exceptions instead)  
❌ Keeping assertions enabled in production (can impact performance)  
❌ Writing assertions with side effects (modifying variables inside an assertion)  
❌ Ignoring failed assertions without investigating  

---

## 🚀 Final Thoughts

- Assertions help ensure **code correctness and reliability**.  
- Use assertions wisely to **catch bugs early**.  
- Always combine assertions with **proper error handling**.  


