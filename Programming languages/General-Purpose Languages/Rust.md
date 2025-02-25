# 🦀 Rust Comprehensive Cheatsheet

## 🔹 Introduction
Rust is a systems programming language that focuses on safety, speed, and concurrency. It prevents memory safety issues without a garbage collector.

```bash
# Install Rust (Linux/macOS)
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

# Verify Installation
rustc --version
```

---

## 🔹 Basic Syntax
```rust
fn main() {
    println!("Hello, World!");
}
```

---

## 🔹 Data Types
```rust
let x: i32 = 42;   // Integer
let y: f64 = 3.14; // Floating point
let z: bool = true; // Boolean
let c: char = 'A';  // Character
let s: &str = "Hello"; // String slice
```

---

## 🔹 Variables & Mutability
```rust
let x = 5; // Immutable by default
let mut y = 10; // Mutable variable
y += 5;
```

---

## 🔹 Control Flow
```rust
if x > 5 {
    println!("Greater than 5");
} else {
    println!("Less than or equal to 5");
}

for i in 0..5 {
    println!("{}", i);
}

let mut counter = 0;
while counter < 5 {
    println!("Counter: {}", counter);
    counter += 1;
}
```

---

## 🔹 Functions
```rust
fn add(x: i32, y: i32) -> i32 {
    x + y // Implicit return
}

fn main() {
    let result = add(5, 3);
    println!("Result: {}", result);
}
```

---

## 🔹 Ownership & Borrowing
```rust
fn main() {
    let s = String::from("hello");
    takes_ownership(s); // Moves ownership
    // println!("{}", s); // ERROR: Value moved
}

fn takes_ownership(some_string: String) {
    println!("{}", some_string);
}
```

```rust
fn main() {
    let s = String::from("hello");
    let len = calculate_length(&s); // Borrowing
    println!("Length: {}", len);
}

fn calculate_length(s: &String) -> usize {
    s.len()
}
```

---

## 🔹 Structs & Enums
```rust
struct Person {
    name: String,
    age: u8,
}

fn main() {
    let person = Person { name: String::from("Alice"), age: 30 };
    println!("{} is {} years old.", person.name, person.age);
}
```

```rust
enum Direction {
    Up,
    Down,
    Left,
    Right,
}

fn main() {
    let movement = Direction::Up;
}
```

---

## 🔹 Traits
```rust
trait Speak {
    fn say_hello(&self);
}

struct Dog;

impl Speak for Dog {
    fn say_hello(&self) {
        println!("Woof!");
    }
}

fn main() {
    let dog = Dog;
    dog.say_hello();
}
```

---

## 🔹 Collections
```rust
let mut v = vec![1, 2, 3];
v.push(4);
println!("Vector: {:?}", v);
```

---

## 🔹 Error Handling
```rust
fn divide(a: f64, b: f64) -> Result<f64, String> {
    if b == 0.0 {
        Err(String::from("Cannot divide by zero"))
    } else {
        Ok(a / b)
    }
}
```

---

## 🔹 Concurrency
```rust
use std::thread;

fn main() {
    let handle = thread::spawn(|| {
        println!("Thread running...");
    });
    handle.join().unwrap();
}
```

---

## 🔹 Macros
```rust
macro_rules! say_hello {
    () => {
        println!("Hello, Macro!");
    };
}

fn main() {
    say_hello!();
}
```

---

## 🔹 File I/O
```rust
use std::fs::File;
use std::io::prelude::*;

fn main() {
    let mut file = File::create("hello.txt").unwrap();
    file.write_all(b"Hello, Rust!").unwrap();
}
```

---

## 🔹 Useful Crates
- `serde` - Serialization/Deserialization
- `tokio` - Async runtime
- `rayon` - Parallelism
- `regex` - Regular expressions

---
