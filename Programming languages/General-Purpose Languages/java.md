# Java Cheat Sheet

## Basics

### Output
```java
System.out.println("Hello, Java!"); // Prints with a newline
System.out.print("Hello");         // Prints without a newline
```

### Comments
- Single-line: `// This is a comment`
- Multi-line:
  ```java
  /*
   This is a multi-line comment
  */
  ```

### Variables and Data Types
```java
int age = 25;            // Integer
float height = 5.9f;     // Float
boolean isActive = true; // Boolean
String name = "John";   // String
```

### Constants
```java
final double PI = 3.14159;
```

## Control Flow

### If/Else
```java
if (condition) {
    // Code if condition is true
} else if (anotherCondition) {
    // Code for another condition
} else {
    // Code if all conditions are false
}
```

### Switch
```java
switch (variable) {
    case 1:
        // Code for case 1
        break;
    case 2:
        // Code for case 2
        break;
    default:
        // Default code
}
```

## Loops

### For Loop
```java
for (int i = 0; i < 10; i++) {
    System.out.println(i);
}
```

### While Loop
```java
while (condition) {
    // Code to execute
}
```

### Do-While Loop
```java
do {
    // Code to execute
} while (condition);
```

### For-Each Loop
```java
for (String item : items) {
    System.out.println(item);
}
```

## Methods

### Defining and Calling Methods
```java
public static int add(int a, int b) {
    return a + b;
}

int sum = add(5, 10);
```

### Method Overloading
```java
public static int multiply(int a, int b) {
    return a * b;
}

public static double multiply(double a, double b) {
    return a * b;
}
```

## Object-Oriented Programming

### Classes and Objects
```java
class Person {
    String name;
    int age;

    Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    void greet() {
        System.out.println("Hello, my name is " + name);
    }
}

Person person = new Person("Alice", 30);
person.greet();
```

### Inheritance
```java
class Animal {
    void sound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("Dog barks");
    }
}

Animal dog = new Dog();
dog.sound();
```

### Interfaces
```java
interface Flyable {
    void fly();
}

class Bird implements Flyable {
    @Override
    public void fly() {
        System.out.println("Bird is flying");
    }
}
```

## Exception Handling

### Try-Catch
```java
try {
    int result = 10 / 0;
} catch (ArithmeticException e) {
    System.out.println("Error: " + e.getMessage());
}
```

### Finally
```java
try {
    int result = 10 / 0;
} catch (Exception e) {
    System.out.println("Error: " + e.getMessage());
} finally {
    System.out.println("This will always execute");
}
```

## Collections

### ArrayList
```java
import java.util.ArrayList;

ArrayList<String> list = new ArrayList<>();
list.add("Apple");
list.add("Banana");
for (String item : list) {
    System.out.println(item);
}
```

### HashMap
```java
import java.util.HashMap;

HashMap<String, Integer> map = new HashMap<>();
map.put("Apple", 3);
map.put("Banana", 5);
System.out.println(map.get("Apple"));
```

## File Handling

### Reading a File
```java
import java.io.*;

try (BufferedReader reader = new BufferedReader(new FileReader("file.txt"))) {
    String line;
    while ((line = reader.readLine()) != null) {
        System.out.println(line);
    }
} catch (IOException e) {
    e.printStackTrace();
}
```

### Writing to a File
```java
import java.io.*;

try (BufferedWriter writer = new BufferedWriter(new FileWriter("file.txt"))) {
    writer.write("Hello, File!");
} catch (IOException e) {
    e.printStackTrace();
}
```

## Debugging

### Print Statements
```java
System.out.println("Debugging information");
```

### Using a Debugger
- Use IDEs like IntelliJ IDEA or Eclipse to set breakpoints and debug your code step by step.

## Best Practices
- Follow naming conventions: camelCase for variables/methods, PascalCase for classes.
- Use meaningful variable names.
- Write comments to explain complex code.
- Handle exceptions appropriately.
- Use unit testing (JUnit) to test your code.

This cheat sheet provides a solid foundation for Java programming, covering both basic and advanced topics.
