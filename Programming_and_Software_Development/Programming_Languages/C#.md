# 🏆 Ultimate C# Cheat Sheet

---

## 📌 1. Introduction to C#

C# (C-Sharp) is a **modern, object-oriented programming language** developed by Microsoft. It is widely used for **desktop applications, web development, game development (Unity), and cloud-based solutions**.

### 🔹 Basic Structure of a C# Program
```csharp
using System;

class Program {
    static void Main() {
        Console.WriteLine("Hello, C#!");
    }
}
```

---

## 📌 2. Variables and Data Types

### 🔹 Declaring Variables
```csharp
int age = 25;
double pi = 3.14;
char grade = 'A';
bool isActive = true;
string name = "Alice";
```

### 🔹 Data Types in C#
| Type      | Description         | Example |
|-----------|---------------------|---------|
| `int`     | Integer number      | `int x = 10;` |
| `double`  | Double-precision    | `double e = 2.718;` |
| `char`    | Single character    | `char ch = 'A';` |
| `bool`    | Boolean (true/false)| `bool isActive = true;` |
| `string`  | String of characters| `string name = "Alice";` |

### 🔹 Constants (`const` and `readonly`)
```csharp
const double PI = 3.14159; // Constant value
readonly int maxScore = 100; // Read-only variable (set in constructor)
```

---

## 📌 3. Operators in C#

### 🔹 Arithmetic Operators
| Operator | Description |
|----------|------------|
| `+` | Addition |
| `-` | Subtraction |
| `*` | Multiplication |
| `/` | Division |
| `%` | Modulus (remainder) |

Example:
```csharp
int a = 10, b = 5;
Console.WriteLine(a + b);  // 15
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
```csharp
if (a > b && b < 10) {
    Console.WriteLine("Both conditions are true");
}
```

---

## 📌 4. Control Flow (Conditions)

### 🔹 If-Else Statement
```csharp
if (x > 10) {
    Console.WriteLine("Greater than 10");
} else {
    Console.WriteLine("10 or less");
}
```

### 🔹 Switch Statement
```csharp
int day = 3;
switch (day) {
    case 1: Console.WriteLine("Monday"); break;
    case 2: Console.WriteLine("Tuesday"); break;
    default: Console.WriteLine("Unknown Day"); break;
}
```

---

## 📌 5. Loops in C#

### 🔹 For Loop
```csharp
for (int i = 1; i <= 5; i++) {
    Console.WriteLine(i);
}
```

### 🔹 While Loop
```csharp
int i = 0;
while (i < 5) {
    Console.WriteLine(i);
    i++;
}
```

### 🔹 Do-While Loop
```csharp
int i = 0;
do {
    Console.WriteLine(i);
    i++;
} while (i < 5);
```

---

## 📌 6. Functions

### 🔹 Declaring and Calling Functions
```csharp
using System;

class Program {
    static int Add(int a, int b) {
        return a + b;
    }

    static void Main() {
        Console.WriteLine("Sum: " + Add(5, 3));
    }
}
```

### 🔹 Method Overloading
```csharp
int Add(int a, int b) { return a + b; }
double Add(double a, double b) { return a + b; }
```

---

## 📌 7. Classes and Objects

### 🔹 Defining a Class and Object
```csharp
class Person {
    public string Name;
    public int Age;

    public void Introduce() {
        Console.WriteLine($"Hi, I'm {Name} and I'm {Age} years old.");
    }
}

class Program {
    static void Main() {
        Person p1 = new Person { Name = "Alice", Age = 25 };
        p1.Introduce();
    }
}
```

### 🔹 Inheritance
```csharp
class Animal {
    public virtual void Sound() {
        Console.WriteLine("Some sound");
    }
}

class Dog : Animal {
    public override void Sound() {
        Console.WriteLine("Bark");
    }
}
```

### 🔹 Constructors
```csharp
class Car {
    public string Brand;

    public Car(string brand) { Brand = brand; } // Constructor

    public void Show() { Console.WriteLine($"Brand: {Brand}"); }
}
```

---

## 📌 8. Exception Handling

```csharp
try {
    int x = 10 / 0;  // Runtime error
} catch (DivideByZeroException e) {
    Console.WriteLine("Cannot divide by zero!");
}
```

---

## 📌 9. Collections

### 🔹 Arrays
```csharp
int[] numbers = {1, 2, 3};
Console.WriteLine(numbers[0]); // 1
```

### 🔹 Lists (`List<T>`)
```csharp
using System.Collections.Generic;

List<int> numbers = new List<int> {1, 2, 3};
numbers.Add(4);
Console.WriteLine(numbers[0]); // 1
```

### 🔹 Dictionaries (`Dictionary<K, V>`)
```csharp
using System.Collections.Generic;

Dictionary<string, int> ageMap = new Dictionary<string, int>();
ageMap["Alice"] = 25;
Console.WriteLine(ageMap["Alice"]); // 25
```

---

## 📌 10. File Handling

### 🔹 Writing to a File
```csharp
using System.IO;

File.WriteAllText("file.txt", "Hello, C#!");
```

### 🔹 Reading from a File
```csharp
string content = File.ReadAllText("file.txt");
Console.WriteLine(content);
```

---

## 📌 11. Asynchronous Programming (Async & Await)

```csharp
using System;
using System.Threading.Tasks;

class Program {
    static async Task Main() {
        await Task.Delay(1000);
        Console.WriteLine("Async Task Completed");
    }
}
```

---
