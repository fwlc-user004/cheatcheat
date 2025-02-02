# Ultimate C Cheat Sheet

---

## **1. Introduction**

C is a powerful, high-performance programming language commonly used for system programming, embedded systems, and application development. It provides direct access to memory and hardware, making it ideal for efficient and optimized software.

### **Basic Structure of a C Program**
Every C program consists of:
- **Preprocessor Directives**: `#include <stdio.h>`
- **Main Function**: `int main()`
- **Statements**: Enclosed in `{}` and ending with `;`
- **Return Statement**: Usually `return 0;` for successful execution.

Example:
```c
#include <stdio.h>

int main() {
    printf("Hello, World!\n");
    return 0;
}
```

---

## **2. Data Types and Variables**

### **Primary Data Types**
| Type      | Description          | Example |
|-----------|----------------------|---------|
| `int`     | Integer (whole number) | `int a = 10;` |
| `float`   | Floating-point number | `float b = 3.14;` |
| `double`  | Double-precision float | `double c = 3.141592;` |
| `char`    | Single character | `char ch = 'A';` |
| `void`    | No type (used in functions) | `void myFunction();` |

### **Variable Declaration**
```c
int age = 25;
float pi = 3.14;
char initial = 'J';
```

### **Constants (`#define` and `const`)**
```c
#define PI 3.14   // Preprocessor constant
const int maxScore = 100;  // Constant variable
```

---

## **3. Operators in C**

### **Arithmetic Operators**
| Operator | Description |
|----------|------------|
| `+` | Addition |
| `-` | Subtraction |
| `*` | Multiplication |
| `/` | Division |
| `%` | Modulus (remainder) |

Example:
```c
int a = 10, b = 5;
int sum = a + b;   // 15
int mod = a % b;   // 0
```

### **Logical and Relational Operators**
| Operator | Description |
|----------|------------|
| `==` | Equal to |
| `!=` | Not equal to |
| `>` | Greater than |
| `<` | Less than |
| `&&` | Logical AND |
| `||` | Logical OR |

Example:
```c
if (a > b && b < 10) {
    printf("Both conditions are true\n");
}
```

---

## **4. Control Flow (Decision Making)**

### **If-Else Statement**
```c
if (x > 10) {
    printf("Greater than 10");
} else {
    printf("10 or less");
}
```

### **Switch Statement**
```c
int day = 3;
switch (day) {
    case 1: printf("Monday\n"); break;
    case 2: printf("Tuesday\n"); break;
    default: printf("Another day\n");
}
```

---

## **5. Loops in C**

### **For Loop**
```c
for (int i = 0; i < 5; i++) {
    printf("%d\n", i);
}
```

### **While Loop**
```c
int i = 0;
while (i < 5) {
    printf("%d\n", i);
    i++;
}
```

### **Do-While Loop**
```c
int i = 0;
do {
    printf("%d\n", i);
    i++;
} while (i < 5);
```

---

## **6. Functions**

Functions make code modular and reusable.

### **Function Declaration and Call**
```c
#include <stdio.h>

int add(int a, int b) {
    return a + b;
}

int main() {
    int sum = add(5, 3);
    printf("Sum: %d\n", sum);
    return 0;
}
```

---

## **7. Pointers**

A pointer stores the memory address of another variable.

### **Declaring and Using Pointers**
```c
int x = 10;
int *ptr = &x;
printf("Address: %p\n", ptr);
printf("Value: %d\n", *ptr);  // Dereferencing pointer
```

---

## **8. Arrays and Strings**

### **Arrays**
```c
int numbers[3] = {1, 2, 3};
printf("%d\n", numbers[0]); // First element
```

### **Strings (Character Arrays)**
```c
char name[] = "Alice";
printf("Hello, %s!", name);
```

---

## **9. Structures in C**

Structures group multiple variables under one name.

```c
struct Person {
    char name[50];
    int age;
};

struct Person p1 = {"Alice", 25};
printf("%s is %d years old", p1.name, p1.age);
```

---

## **10. File Handling**

### **Writing to a File**
```c
#include <stdio.h>

int main() {
    FILE *fptr = fopen("file.txt", "w");
    fprintf(fptr, "Hello, File Handling!");
    fclose(fptr);
    return 0;
}
```

### **Reading from a File**
```c
#include <stdio.h>

int main() {
    char buffer[100];
    FILE *fptr = fopen("file.txt", "r");
    fgets(buffer, 100, fptr);
    printf("%s", buffer);
    fclose(fptr);
    return 0;
}
```

---

## **11. Memory Management**

C provides dynamic memory allocation through `malloc()` and `free()`.

```c
#include <stdlib.h>

int *ptr = (int*) malloc(sizeof(int));
free(ptr);
```

---

## **12. Preprocessor Directives**

| Directive | Description |
|-----------|------------|
| `#define` | Define macros |
| `#include` | Include header files |
| `#ifdef` | Conditional compilation |
| `#ifndef` | Check if not defined |

Example:
```c
#define PI 3.14
#include <stdio.h>
```

---

## **13. Common Standard Library Functions**

### **String Manipulation (`string.h`)**
```c
#include <string.h>
strlen(str);   // Get string length
strcpy(dest, src); // Copy string
strcmp(str1, str2); // Compare strings
```

### **Math Functions (`math.h`)**
```c
#include <math.h>
pow(2, 3);   // 2^3
sqrt(16);    // Square root of 16
```

### **Standard Library (`stdlib.h`)**
```c
#include <stdlib.h>
atoi("123");   // Convert string to integer
rand();        // Generate a random number
```

---
