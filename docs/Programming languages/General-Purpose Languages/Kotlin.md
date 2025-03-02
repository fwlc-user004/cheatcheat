# 🏆 Ultimate Kotlin Cheat Sheet

---

## 📌 1. Introduction to Kotlin

Kotlin is a modern, statically-typed programming language developed by **JetBrains**. It is officially supported for Android development and can be used for backend, frontend, and multiplatform development.

### 🔹 Key Features of Kotlin
- **Concise**: Less boilerplate code compared to Java.
- **Safe**: Null safety to reduce `NullPointerException` (NPE) errors.
- **Interoperable**: Works seamlessly with Java.
- **Functional Programming**: Supports higher-order functions and lambdas.

### 🔹 Basic Structure of a Kotlin Program
```kotlin
fun main() {
    println("Hello, Kotlin!")
}
```

---

## 📌 2. Variables and Data Types

### 🔹 Declaring Variables
Kotlin has two ways to declare variables:
```kotlin
val name = "Alice"   // Immutable (read-only)
var age = 25         // Mutable (modifiable)
```
- `val` (value) **cannot be reassigned** (like `final` in Java).
- `var` (variable) **can be reassigned**.

### 🔹 Kotlin Data Types
| Type      | Description          | Example |
|-----------|----------------------|---------|
| `Int`     | Integer numbers | `val number: Int = 10` |
| `Double`  | Floating-point | `val pi: Double = 3.14` |
| `Boolean` | True/False | `val isActive: Boolean = true` |
| `Char`    | Single character | `val letter: Char = 'A'` |
| `String`  | Textual data | `val name: String = "Kotlin"` |
| `Any`     | Can store any type | `val anything: Any = 42` |

### 🔹 Type Conversion
```kotlin
val num = 10
val doubleNum = num.toDouble()   // Converts Int to Double
val str = num.toString()         // Converts Int to String
```

---

## 📌 3. Control Flow (Conditions)

### 🔹 If-Else Statement
```kotlin
val num = 10
if (num > 5) {
    println("Greater than 5")
} else {
    println("Less than or equal to 5")
}
```

### 🔹 When Statement (Alternative to `switch`)
```kotlin
val day = 3
val result = when (day) {
    1 -> "Monday"
    2 -> "Tuesday"
    3 -> "Wednesday"
    else -> "Unknown Day"
}
println(result)
```

---

## 📌 4. Loops

### 🔹 For Loop
```kotlin
for (i in 1..5) {
    println(i)  // Prints numbers from 1 to 5
}
```

### 🔹 While Loop
```kotlin
var i = 0
while (i < 5) {
    println(i)
    i++
}
```

### 🔹 Do-While Loop
```kotlin
var i = 0
do {
    println(i)
    i++
} while (i < 5)
```

---

## 📌 5. Functions

### 🔹 Declaring and Calling Functions
```kotlin
fun greet(name: String): String {
    return "Hello, $name!"
}

fun main() {
    println(greet("Alice"))
}
```

### 🔹 Inline Functions (Single Expression)
```kotlin
fun square(num: Int) = num * num
println(square(5))  // 25
```

### 🔹 Higher-Order Functions (Passing Functions as Arguments)
```kotlin
fun operate(x: Int, y: Int, op: (Int, Int) -> Int): Int {
    return op(x, y)
}

val sum = operate(5, 3) { a, b -> a + b }
println(sum)  // 8
```

---

## 📌 6. Object-Oriented Programming (OOP)

### 🔹 Defining a Class
```kotlin
class Person(val name: String, var age: Int) {
    fun greet() = "Hi, I'm $name and I'm $age years old."
}

val p = Person("Alice", 25)
println(p.greet())
```

### 🔹 Inheritance
```kotlin
open class Animal {
    open fun makeSound() = "Some sound"
}

class Dog : Animal() {
    override fun makeSound() = "Bark"
}

val dog = Dog()
println(dog.makeSound())  // Bark
```

### 🔹 Data Classes (For Storing Data)
```kotlin
data class User(val name: String, val age: Int)

val user = User("Alice", 30)
println(user.name)  // Alice
```

---

## 📌 7. Collections

### 🔹 Lists
```kotlin
val numbers = listOf(1, 2, 3, 4, 5)  // Immutable List
val mutableNumbers = mutableListOf(1, 2, 3) // Mutable List

mutableNumbers.add(4)
println(mutableNumbers)  // [1, 2, 3, 4]
```

### 🔹 Sets
```kotlin
val uniqueNumbers = setOf(1, 2, 3, 3, 4)
println(uniqueNumbers)  // [1, 2, 3, 4]
```

### 🔹 Maps (Key-Value Pairs)
```kotlin
val person = mapOf("name" to "Alice", "age" to 25)
println(person["name"])  // Alice
```

---

## 📌 8. Null Safety

Kotlin eliminates the `NullPointerException` issue by making **nullability explicit**.

### 🔹 Nullable Variables
```kotlin
var name: String? = null
println(name?.length)  // Safe call operator "?."
```

### 🔹 Elvis Operator (`?:`) (Providing Default Value)
```kotlin
val length = name?.length ?: 0  // If name is null, return 0
```

### 🔹 Non-Null Assertion (`!!`)
```kotlin
val length = name!!.length  // Throws exception if name is null
```

---

## 📌 9. Exception Handling

```kotlin
try {
    val num = "abc".toInt()
} catch (e: NumberFormatException) {
    println("Invalid number format!")
} finally {
    println("Execution completed.")
}
```

---

## 📌 10. File Handling

### 🔹 Writing to a File
```kotlin
import java.io.File

File("output.txt").writeText("Hello, Kotlin!")
```

### 🔹 Reading from a File
```kotlin
val content = File("output.txt").readText()
println(content)
```

---

## 📌 11. Coroutines (Asynchronous Programming)

Kotlin provides **coroutines** for efficient asynchronous programming.

```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {
    launch {
        delay(1000L)
        println("World!")
    }
    println("Hello,")
}
```

---
