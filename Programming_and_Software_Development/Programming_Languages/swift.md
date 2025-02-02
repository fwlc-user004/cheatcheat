# 🏆 Ultimate Swift Cheat Sheet

---

## 📌 1. Introduction to Swift

Swift is a **modern, safe, and fast** programming language developed by **Apple**. It is used for **iOS, macOS, watchOS, and tvOS** app development.

### 🔹 Basic Structure of a Swift Program
```swift
import Foundation

print("Hello, Swift!")
```

---

## 📌 2. Variables and Data Types

### 🔹 Declaring Variables
```swift
var age = 25       // Mutable variable
let pi = 3.14      // Immutable constant
var name: String = "Alice" // Explicit type declaration
```

### 🔹 Swift Data Types
| Type      | Description          | Example |
|-----------|----------------------|---------|
| `Int`     | Integer numbers | `var number: Int = 10` |
| `Double`  | Floating-point | `var pi: Double = 3.14` |
| `Bool`    | True/False | `var isActive: Bool = true` |
| `Character` | Single character | `var letter: Character = "A"` |
| `String`  | Textual data | `var name: String = "Swift"` |
| `Any`     | Can store any type | `var anything: Any = 42` |

### 🔹 Type Conversion
```swift
let num = 10
let doubleNum = Double(num)  // Convert Int to Double
let str = String(num)        // Convert Int to String
```

---

## 📌 3. Control Flow (Conditions)

### 🔹 If-Else Statement
```swift
let num = 10
if num > 5 {
    print("Greater than 5")
} else {
    print("Less than or equal to 5")
}
```

### 🔹 Switch Statement
```swift
let day = 3
switch day {
case 1:
    print("Monday")
case 2:
    print("Tuesday")
case 3:
    print("Wednesday")
default:
    print("Unknown Day")
}
```

---

## 📌 4. Loops

### 🔹 For Loop
```swift
for i in 1...5 {
    print(i)  // Prints numbers from 1 to 5
}
```

### 🔹 While Loop
```swift
var i = 0
while i < 5 {
    print(i)
    i += 1
}
```

### 🔹 Repeat-While Loop (Do-While)
```swift
var i = 0
repeat {
    print(i)
    i += 1
} while i < 5
```

---

## 📌 5. Functions

### 🔹 Declaring and Calling Functions
```swift
func greet(name: String) -> String {
    return "Hello, \(name)!"
}

print(greet(name: "Alice"))
```

### 🔹 Function with Default Parameters
```swift
func sayHello(to name: String = "Guest") {
    print("Hello, \(name)!")
}

sayHello()         // Hello, Guest!
sayHello(to: "Bob") // Hello, Bob!
```

### 🔹 Higher-Order Functions (Passing Functions as Arguments)
```swift
func operate(a: Int, b: Int, operation: (Int, Int) -> Int) -> Int {
    return operation(a, b)
}

let sum = operate(a: 5, b: 3) { $0 + $1 }
print(sum)  // 8
```

---

## 📌 6. Object-Oriented Programming (OOP)

### 🔹 Defining a Class
```swift
class Person {
    var name: String
    var age: Int

    init(name: String, age: Int) {
        self.name = name
        self.age = age
    }

    func greet() -> String {
        return "Hi, I'm \(name) and I'm \(age) years old."
    }
}

let p = Person(name: "Alice", age: 25)
print(p.greet())
```

### 🔹 Inheritance
```swift
class Animal {
    func makeSound() -> String {
        return "Some sound"
    }
}

class Dog: Animal {
    override func makeSound() -> String {
        return "Bark"
    }
}

let dog = Dog()
print(dog.makeSound())  // Bark
```

### 🔹 Structs (Value Types)
```swift
struct Car {
    var brand: String

    func show() {
        print("Brand: \(brand)")
    }
}

let car = Car(brand: "Tesla")
car.show()  // Brand: Tesla
```

---

## 📌 7. Collections

### 🔹 Arrays
```swift
var numbers = [1, 2, 3, 4, 5]
numbers.append(6)
print(numbers[0])  // 1
```

### 🔹 Sets (Unique Elements)
```swift
var uniqueNumbers: Set = [1, 2, 3, 3, 4]
print(uniqueNumbers)  // {1, 2, 3, 4}
```

### 🔹 Dictionaries (Key-Value Pairs)
```swift
var person: [String: Any] = ["name": "Alice", "age": 25]
print(person["name"] as! String)  // Alice
```

---

## 📌 8. Optionals and Null Safety

Swift provides **optionals** to handle `nil` safely.

### 🔹 Declaring an Optional
```swift
var name: String? = nil
print(name ?? "No name")  // Provides default value
```

### 🔹 Optional Binding
```swift
if let safeName = name {
    print(safeName)
} else {
    print("No name found")
}
```

### 🔹 Forced Unwrapping (Only if you're sure it's not nil)
```swift
let length = name!.count  // Causes crash if name is nil
```

---

## 📌 9. Error Handling

```swift
enum FileError: Error {
    case fileNotFound
}

func readFile(filename: String) throws {
    throw FileError.fileNotFound
}

do {
    try readFile(filename: "test.txt")
} catch {
    print("An error occurred: \(error)")
}
```

---

## 📌 10. File Handling

### 🔹 Writing to a File
```swift
import Foundation

let content = "Hello, Swift!"
try content.write(toFile: "output.txt", atomically: true, encoding: .utf8)
```

### 🔹 Reading from a File
```swift
let content = try String(contentsOfFile: "output.txt", encoding: .utf8)
print(content)
```

---

## 📌 11. Asynchronous Programming (Concurrency)

```swift
import Foundation

func fetchData() async {
    try await Task.sleep(nanoseconds: 1_000_000_000)
    print("Data fetched!")
}

Task {
    await fetchData()
}
```

---
