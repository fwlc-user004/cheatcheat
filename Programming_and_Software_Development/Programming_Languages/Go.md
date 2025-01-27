# Ultimate Go (Golang) Cheat Sheet

---

## **1. Basics**

### Hello, World!
```go
package main

import "fmt"

func main() {
    fmt.Println("Hello, World!")
}
```

### Variables and Constants
```go
var name string = "Alice" // Explicit type
age := 25                 // Implicit type
const Pi = 3.14159        // Constant
```

### Data Types
```go
var (
    i int     // Integer
    f float64 // Float
    s string  // String
    b bool    // Boolean
)
```

### Printing
```go
fmt.Printf("Name: %s, Age: %d\n", name, age)
```

---

## **2. Control Flow**

### If-Else
```go
if age > 18 {
    fmt.Println("Adult")
} else {
    fmt.Println("Minor")
}
```

### For Loop
```go
for i := 0; i < 5; i++ {
    fmt.Println(i)
}
```

### Switch
```go
switch day := "Monday"; day {
case "Monday":
    fmt.Println("Start of the week")
case "Friday":
    fmt.Println("End of the week")
default:
    fmt.Println("Midweek")
}
```

---

## **3. Functions**

### Basic Function
```go
func add(a int, b int) int {
    return a + b
}
```

### Multiple Return Values
```go
func divide(a, b int) (int, int) {
    return a / b, a % b
}
```

### Variadic Functions
```go
func sum(nums ...int) int {
    total := 0
    for _, n := range nums {
        total += n
    }
    return total
}
```

---

## **4. Collections**

### Arrays
```go
var arr = [3]int{1, 2, 3}
fmt.Println(arr[0])
```

### Slices
```go
slice := []int{1, 2, 3}
slice = append(slice, 4)
fmt.Println(slice)
```

### Maps
```go
m := make(map[string]int)
m["Alice"] = 25
fmt.Println(m["Alice"])
```

### Iterating Over Collections
```go
for key, value := range m {
    fmt.Printf("%s -> %d\n", key, value)
}
```

---

## **5. Structs and Methods**

### Defining a Struct
```go
type Person struct {
    Name string
    Age  int
}
```

### Methods
```go
func (p Person) Greet() string {
    return fmt.Sprintf("Hi, I'm %s and I'm %d years old.", p.Name, p.Age)
}
```

### Pointer Receivers
```go
func (p *Person) UpdateName(newName string) {
    p.Name = newName
}
```

---

## **6. Goroutines and Channels**

### Goroutines
```go
func sayHello() {
    fmt.Println("Hello")
}

go sayHello()
```

### Channels
```go
ch := make(chan int)
go func() {
    ch <- 42
}()
fmt.Println(<-ch)
```

### Buffered Channels
```go
ch := make(chan int, 2)
ch <- 1
ch <- 2
fmt.Println(<-ch)
fmt.Println(<-ch)
```

---

## **7. Error Handling**

### Basic Error Handling
```go
import "errors"

func divide(a, b int) (int, error) {
    if b == 0 {
        return 0, errors.New("cannot divide by zero")
    }
    return a / b, nil
}

result, err := divide(10, 0)
if err != nil {
    fmt.Println(err)
} else {
    fmt.Println(result)
}
```

### Panic and Recover
```go
func riskyFunction() {
    defer func() {
        if r := recover(); r != nil {
            fmt.Println("Recovered from:", r)
        }
    }()
    panic("Something went wrong!")
}

riskyFunction()
```

---

## **8. Interfaces**

### Defining and Using Interfaces
```go
type Shape interface {
    Area() float64
}

type Circle struct {
    Radius float64
}

func (c Circle) Area() float64 {
    return 3.14 * c.Radius * c.Radius
}

var s Shape = Circle{Radius: 5}
fmt.Println(s.Area())
```

---

## **9. File Handling**

### Reading a File
```go
import (
    "io/ioutil"
    "log"
)

data, err := ioutil.ReadFile("file.txt")
if err != nil {
    log.Fatal(err)
}
fmt.Println(string(data))
```

### Writing to a File
```go
err := ioutil.WriteFile("file.txt", []byte("Hello, File!"), 0644)
if err != nil {
    log.Fatal(err)
}
```

---

## **10. Testing**

### Basic Testing
```go
import "testing"

func TestAdd(t *testing.T) {
    result := add(2, 3)
    if result != 5 {
        t.Errorf("Expected 5 but got %d", result)
    }
}
```

---

## **11. Tips and Tricks**

### Defer
```go
defer fmt.Println("This is deferred")
fmt.Println("End of function")
```

### Zero Values
```go
var x int     // Defaults to 0
var y string  // Defaults to ""
var z bool    // Defaults to false
```

### Short Variable Declaration
```go
x := 10  // Equivalent to var x int = 10
```

---

## **12. Go Modules**

### Initialize a Module
```bash
go mod init <module_name>
```

### Add Dependencies
```bash
go get <package_name>
```

### Tidy Up
```bash
go mod tidy
```

---

Elevate your Go programming skills with this ultimate cheat sheet! 🚀

