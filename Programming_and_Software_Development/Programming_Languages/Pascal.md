# 🏆 Ultimate Pascal Cheat Sheet

---

## 📌 1. Introduction to Pascal

**Pascal** is a structured, procedural programming language designed for **teaching, system programming, and software development**.

### 🔹 Basic Structure of a Pascal Program
```pascal
program HelloWorld;
begin
    writeln('Hello, Pascal!');
end.
```

### 🔹 Compiling and Running Pascal Code
- Use **Free Pascal Compiler (FPC)**: `fpc program.pas`
- Run the compiled program: `./program`

---

## 📌 2. Variables and Data Types

### 🔹 Declaring Variables
```pascal
var
    age: Integer;
    pi: Real;
    name: String;
    isActive: Boolean;
begin
    age := 25;
    pi := 3.14;
    name := 'Alice';
    isActive := True;
end.
```

### 🔹 Common Data Types in Pascal
| Type      | Description          | Example |
|-----------|----------------------|---------|
| `Integer` | Whole number         | `var x: Integer;` |
| `Real`    | Floating-point number| `var y: Real;` |
| `Char`    | Single character     | `var ch: Char;` |
| `String`  | Sequence of characters | `var s: String;` |
| `Boolean` | True/False value     | `var isReady: Boolean;` |

---

## 📌 3. Operators

### 🔹 Arithmetic Operators
| Operator | Description |
|----------|------------|
| `+` | Addition |
| `-` | Subtraction |
| `*` | Multiplication |
| `/` | Division |
| `div` | Integer Division |
| `mod` | Modulus (remainder) |

Example:
```pascal
var sum, remainder: Integer;
begin
    sum := 10 + 5;      { 15 }
    remainder := 10 mod 3; { 1 }
end.
```

### 🔹 Logical Operators
| Operator | Description |
|----------|------------|
| `and` | Logical AND |
| `or`  | Logical OR |
| `not` | Logical NOT |

Example:
```pascal
if (x > 5) and (y < 10) then writeln('Condition met');
```

---

## 📌 4. Control Flow

### 🔹 If-Else Statement
```pascal
if x > 10 then
    writeln('Greater than 10')
else
    writeln('10 or less');
```

### 🔹 Case Statement (Switch Alternative)
```pascal
case day of
    1: writeln('Monday');
    2: writeln('Tuesday');
    else writeln('Another day');
end;
```

---

## 📌 5. Loops

### 🔹 For Loop
```pascal
for i := 1 to 5 do
    writeln(i);
```

### 🔹 While Loop
```pascal
while x < 10 do
begin
    writeln(x);
    x := x + 1;
end;
```

### 🔹 Repeat-Until Loop
```pascal
repeat
    writeln(x);
    x := x + 1;
until x > 10;
```

---

## 📌 6. Functions and Procedures

### 🔹 Function (Returns a Value)
```pascal
function AddNumbers(a, b: Integer): Integer;
begin
    AddNumbers := a + b;
end;

begin
    writeln(AddNumbers(5, 3));
end.
```

### 🔹 Procedure (No Return Value)
```pascal
procedure Greet(name: String);
begin
    writeln('Hello, ', name, '!');
end;

begin
    Greet('Alice');
end.
```

---

## 📌 7. Arrays and Strings

### 🔹 Declaring Arrays
```pascal
var numbers: array[1..5] of Integer;
begin
    numbers[1] := 10;
    writeln(numbers[1]);
end.
```

### 🔹 Strings Manipulation
```pascal
var name: String;
begin
    name := 'Pascal';
    writeln('Length: ', Length(name));
end.
```

---

## 📌 8. File Handling

### 🔹 Writing to a File
```pascal
var f: Text;
begin
    Assign(f, 'output.txt');
    Rewrite(f);
    writeln(f, 'Hello, File!');
    Close(f);
end.
```

### 🔹 Reading from a File
```pascal
var f: Text;
    line: String;
begin
    Assign(f, 'output.txt');
    Reset(f);
    while not EOF(f) do
    begin
        Readln(f, line);
        writeln(line);
    end;
    Close(f);
end.
```

---

## 📌 9. Pointers

### 🔹 Using Pointers in Pascal
```pascal
var ptr: ^Integer;
    num: Integer;
begin
    num := 10;
    ptr := @num;
    writeln('Pointer Value: ', ptr^);
end.
```

---

## 📌 10. Records (Struct Alternative)

### 🔹 Defining and Using Records
```pascal
type
    Person = record
        name: String;
        age: Integer;
    end;

var p: Person;
begin
    p.name := 'Alice';
    p.age := 25;
    writeln(p.name, ' is ', p.age, ' years old.');
end.
```

---

## 📌 11. Object-Oriented Pascal

### 🔹 Creating a Class
```pascal
type
    TPerson = class
        name: String;
        age: Integer;
        procedure Introduce;
    end;

procedure TPerson.Introduce;
begin
    writeln('Hi, I am ', name, ' and I am ', age, ' years old.');
end;

var p: TPerson;
begin
    p := TPerson.Create;
    p.name := 'Alice';
    p.age := 25;
    p.Introduce;
end.
```

---
