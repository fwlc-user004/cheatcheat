# 🏆 Ultimate C++ Cheat Sheet

---

## 📌 1. Introduction to C++

C++ is a powerful, general-purpose programming language that extends **C** with **object-oriented**, **functional**, and **generic programming** features. It is widely used for system programming, game development, and high-performance applications.

### 🔹 Basic Structure of a C++ Program
```cpp
#include <iostream>
using namespace std;

int main() {
    cout << "Hello, C++!" << endl;
    return 0;
}
```

---

## 📌 2. Variables and Data Types

### 🔹 Declaring Variables
```cpp
int age = 25;
float pi = 3.14;
char grade = 'A';
bool isActive = true;
string name = "Alice";
```

### 🔹 Data Types in C++
| Type      | Description         | Example |
|-----------|---------------------|---------|
| `int`     | Integer number      | `int x = 10;` |
| `float`   | Floating-point      | `float pi = 3.14;` |
| `double`  | Double-precision    | `double e = 2.718;` |
| `char`    | Single character    | `char ch = 'A';` |
| `bool`    | Boolean (true/false)| `bool isActive = true;` |
| `string`  | String of characters| `string name = "Alice";` |

### 🔹 Constants (`const` and `#define`)
```cpp
const double PI = 3.14159; // Constant variable
#define MAX_SCORE 100 // Preprocessor constant
```

---

## 📌 3. Operators in C++

### 🔹 Arithmetic Operators
| Operator | Description |
|----------|------------|
| `+` | Addition |
| `-` | Subtraction |
| `*` | Multiplication |
| `/` | Division |
| `%` | Modulus (remainder) |

Example:
```cpp
int a = 10, b = 5;
cout << a + b;  // 15
```

### 🔹 Logical and Relational Operators
| Operator | Description |
|----------|------------|
| `==` | Equal to |
| `!=` | Not equal to |
| `>` | Greater than |
| `<` | Less than |
| `&&` | Logical AND |
| `||` | Logical OR |

Example:
```cpp
if (a > b && b < 10) {
    cout << "Both conditions are true";
}
```

---

## 📌 4. Control Flow (Conditions)

### 🔹 If-Else Statement
```cpp
if (x > 10) {
    cout << "Greater than 10";
} else {
    cout << "10 or less";
}
```

### 🔹 Switch Statement
```cpp
int day = 3;
switch (day) {
    case 1: cout << "Monday"; break;
    case 2: cout << "Tuesday"; break;
    default: cout << "Unknown Day";
}
```

---

## 📌 5. Loops in C++

### 🔹 For Loop
```cpp
for (int i = 1; i <= 5; i++) {
    cout << i << endl;
}
```

### 🔹 While Loop
```cpp
int i = 0;
while (i < 5) {
    cout << i << endl;
    i++;
}
```

### 🔹 Do-While Loop
```cpp
int i = 0;
do {
    cout << i << endl;
    i++;
} while (i < 5);
```

---

## 📌 6. Functions

### 🔹 Declaring and Calling Functions
```cpp
#include <iostream>
using namespace std;

int add(int a, int b) {
    return a + b;
}

int main() {
    cout << "Sum: " << add(5, 3) << endl;
    return 0;
}
```

### 🔹 Function Overloading
```cpp
int add(int a, int b) { return a + b; }
double add(double a, double b) { return a + b; }
```

---

## 📌 7. Pointers

### 🔹 Declaring and Using Pointers
```cpp
int x = 10;
int *ptr = &x;
cout << "Address: " << ptr << endl;
cout << "Value: " << *ptr << endl;
```

---

## 📌 8. Arrays and Strings

### 🔹 Arrays
```cpp
int numbers[3] = {1, 2, 3};
cout << numbers[0];  // First element
```

### 🔹 Strings (Using `string` Class)
```cpp
string name = "Alice";
cout << "Hello, " << name << "!";
```

---

## 📌 9. Object-Oriented Programming (OOP)

### 🔹 Classes and Objects
```cpp
class Person {
public:
    string name;
    int age;

    void introduce() {
        cout << "Hi, I'm " << name << " and I'm " << age << " years old." << endl;
    }
};

int main() {
    Person p1;
    p1.name = "Alice";
    p1.age = 25;
    p1.introduce();
    return 0;
}
```

### 🔹 Inheritance
```cpp
class Animal {
public:
    void sound() {
        cout << "Some sound" << endl;
    }
};

class Dog : public Animal {
public:
    void sound() {
        cout << "Bark" << endl;
    }
};
```

### 🔹 Constructors
```cpp
class Car {
public:
    string brand;

    Car(string b) { brand = b; } // Constructor

    void show() { cout << "Brand: " << brand << endl; }
};
```

---

## 📌 10. File Handling

### 🔹 Writing to a File
```cpp
#include <fstream>

ofstream myFile("file.txt");
myFile << "Hello, C++!";
myFile.close();
```

### 🔹 Reading from a File
```cpp
#include <fstream>

ifstream myFile("file.txt");
string content;
while (getline(myFile, content)) {
    cout << content << endl;
}
myFile.close();
```

---

## 📌 11. Exception Handling

```cpp
try {
    int x = 10 / 0;  // Runtime error
} catch (...) {
    cout << "An error occurred!";
}
```

---

## 📌 12. Standard Template Library (STL)

### 🔹 Vectors (Dynamic Arrays)
```cpp
#include <vector>
vector<int> v = {1, 2, 3};
v.push_back(4);
cout << v[0];  // 1
```

### 🔹 Maps (Key-Value Pairs)
```cpp
#include <map>
map<string, int> ageMap;
ageMap["Alice"] = 25;
cout << ageMap["Alice"];
```

---
