# Ultimate Python Cheat Sheet

---

## **1. Basics**

### Hello, World!
```python
print("Hello, World!")
```

### Variables and Data Types
```python
x = 10         # Integer
y = 3.14       # Float
name = "Alice" # String
is_active = True # Boolean
z = 1 + 2j     # Complex number
```

### Type Checking and Conversion
```python
# Type checking
print(type(x))        # <class 'int'>
print(isinstance(x, int)) # True

# Type conversion
x = str(123)         # "123"
y = int("456")       # 456
z = float("3.14")    # 3.14
```

### Comments
```python
# This is a single-line comment
""" This is a 
multi-line comment """
```

---

## **2. Strings**

### String Operations
```python
s = "Python"
print(s.upper())       # PYTHON
print(s.lower())       # python
print(s.startswith("Py")) # True
print(s.endswith("on"))   # True
print(len(s))          # 6
```

### String Formatting
```python
name = "Alice"
age = 25
print(f"{name} is {age} years old.")
print("{0} is {1} years old.".format(name, age))
```

### String Slicing
```python
s = "Python"
print(s[0])    # P
print(s[-1])   # n
print(s[1:4])  # yth
```

---

## **3. Collections**

### Lists
```python
my_list = [1, 2, 3, 4]
my_list.append(5)
print(my_list)        # [1, 2, 3, 4, 5]
print(my_list[2])     # 3
```

### Tuples
```python
t = (1, 2, 3)
print(t[0])           # 1
```

### Dictionaries
```python
d = {"name": "Alice", "age": 25}
print(d["name"])      # Alice
print(d.keys())        # dict_keys(['name', 'age'])
print(d.values())      # dict_values(['Alice', 25])
```

### Sets
```python
my_set = {1, 2, 3, 3}
print(my_set)         # {1, 2, 3}
```

---

## **4. Control Flow**

### If-Else
```python
x = 10
if x > 5:
    print("Greater than 5")
else:
    print("5 or less")
```

### Loops
```python
# For Loop
for i in range(5):
    print(i)

# While Loop
x = 0
while x < 5:
    print(x)
    x += 1
```

---

## **5. Functions**

### Define and Call Functions
```python
def greet(name):
    return f"Hello, {name}!"

print(greet("Alice"))
```

### Lambda Functions
```python
square = lambda x: x ** 2
print(square(5))        # 25
```

---

## **6. Classes and Objects**

### Define a Class
```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def greet(self):
        return f"Hi, I'm {self.name} and I'm {self.age} years old."

p = Person("Alice", 25)
print(p.greet())
```

---

## **7. File Handling**

### Read a File
```python
with open("file.txt", "r") as f:
    content = f.read()
    print(content)
```

### Write to a File
```python
with open("file.txt", "w") as f:
    f.write("Hello, File!")
```

---

## **8. Modules**

### Importing Modules
```python
import math
print(math.sqrt(16))     # 4.0
```

### From Module Import
```python
from math import pi
print(pi)                # 3.141592653589793
```

---

## **9. Error Handling**

### Try-Except
```python
try:
    x = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero!")
finally:
    print("Execution completed")
```

---

## **10. Advanced Topics**

### List Comprehensions
```python
squared = [x**2 for x in range(5)]
print(squared)          # [0, 1, 4, 9, 16]
```

### Generators
```python
def gen():
    yield 1
    yield 2
    yield 3

for value in gen():
    print(value)
```

### Decorators
```python
def decorator(func):
    def wrapper():
        print("Before the function call")
        func()
        print("After the function call")
    return wrapper

@decorator
def say_hello():
    print("Hello!")

say_hello()
```

### Asynchronous Programming
```python
import asyncio

async def main():
    print("Hello")
    await asyncio.sleep(1)
    print("World")

asyncio.run(main())
```

---

## **11. Popular Libraries**

### NumPy
```python
import numpy as np
arr = np.array([1, 2, 3])
print(arr.mean())
```

### Pandas
```python
import pandas as pd
data = {"Name": ["Alice", "Bob"], "Age": [25, 30]}
df = pd.DataFrame(data)
print(df)
```

### Matplotlib
```python
import matplotlib.pyplot as plt
x = [1, 2, 3]
y = [4, 5, 6]
plt.plot(x, y)
plt.show()
```

### Requests
```python
import requests
response = requests.get("https://api.example.com")
print(response.text)
```

### TensorFlow
```python
import tensorflow as tf
print(tf.constant("Hello, TensorFlow!"))
```

---

## **12. Best Practices**

### Coding Standards
- Follow **PEP 8** guidelines for Python code.
- Use descriptive variable and function names.

### Virtual Environments
```bash
python -m venv env
source env/bin/activate  # On Linux/Mac
env\Scripts\activate    # On Windows
```

### Type Hints
```python
def add(a: int, b: int) -> int:
    return a + b
```

### Testing
```python
import unittest

class TestMath(unittest.TestCase):
    def test_add(self):
        self.assertEqual(add(2, 3), 5)

if __name__ == "__main__":
    unittest.main()
```

---

## **13. Debugging**

### Debugging with `pdb`
```python
import pdb
pdb.set_trace()
```

### Using Logging
```python
import logging
logging.basicConfig(level=logging.DEBUG)
logging.debug("This is a debug message")
```

---

## **14. Tips and Tricks**

### Unpack Variables
```python
x, y, z = [1, 2, 3]
print(x, y, z)           # 1 2 3
```

### Enumerate
```python
items = ["a", "b", "c"]
for index, value in enumerate(items):
    print(index, value)
```

### Zip
```python
names = ["Alice", "Bob"]
ages = [25, 30]
for name, age in zip(names, ages):
    print(name, age)
```

### Profiling
```python
import cProfile
cProfile.run('sum(range(1000))')
```

### Map, Filter, Reduce
```python
from functools import reduce
nums = [1, 2, 3, 4]

# Map
squared = list(map(lambda x: x**2, nums))

# Filter
evens = list(filter(lambda x: x % 2 == 0, nums))

# Reduce
product = reduce(lambda x, y: x * y, nums)
```

---

Elevate your Python programming skills with this expanded and ultimate cheat sheet! 🚀
