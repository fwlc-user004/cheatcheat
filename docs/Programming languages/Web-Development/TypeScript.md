# 🚀 TypeScript Comprehensive Cheatsheet

## 🔹 Installing TypeScript
```sh
# Install TypeScript globally
npm install -g typescript

# Check version
tsc --version

# Compile TypeScript to JavaScript
tsc file.ts
```

## 🔹 Type Annotations
```ts
let count: number = 10;
let username: string = "Alice";
let isLoggedIn: boolean = true;
let numbers: number[] = [1, 2, 3];
let tuple: [string, number] = ["John", 25];
```

## 🔹 Functions
```ts
function add(a: number, b: number): number {
    return a + b;
}

const multiply = (a: number, b: number): number => a * b;
```

## 🔹 Interfaces
```ts
interface User {
    id: number;
    name: string;
    email?: string; // Optional property
}

const user: User = {
    id: 1,
    name: "Alice"
};
```

## 🔹 Type Aliases
```ts
type Point = {
    x: number;
    y: number;
};

const point: Point = { x: 10, y: 20 };
```

## 🔹 Union & Intersection Types
```ts
let value: string | number;
value = "Hello";
value = 42;

interface A {
    a: string;
}
interface B {
    b: number;
}

const obj: A & B = { a: "Hello", b: 42 };
```

## 🔹 Enums
```ts
enum Direction {
    Up,
    Down,
    Left,
    Right
}

let move: Direction = Direction.Up;
```

## 🔹 Generics
```ts
function identity<T>(arg: T): T {
    return arg;
}

let output = identity<string>("Hello");
```

## 🔹 Classes
```ts
class Person {
    private id: number;
    public name: string;

    constructor(id: number, name: string) {
        this.id = id;
        this.name = name;
    }

    greet(): void {
        console.log(`Hello, my name is ${this.name}`);
    }
}

const person1 = new Person(1, "Alice");
person1.greet();
```

## 🔹 Access Modifiers
```ts
class Animal {
    public name: string;
    private age: number;
    protected species: string;

    constructor(name: string, age: number, species: string) {
        this.name = name;
        this.age = age;
        this.species = species;
    }
}
```

## 🔹 Abstract Classes
```ts
abstract class Shape {
    abstract getArea(): number;
}

class Circle extends Shape {
    constructor(public radius: number) {
        super();
    }
    getArea(): number {
        return Math.PI * this.radius ** 2;
    }
}
```

## 🔹 Interfaces vs Type Aliases
```ts
interface Car {
    brand: string;
    year: number;
}

type Truck = {
    brand: string;
    capacity: number;
};
```

## 🔹 Type Assertions
```ts
let someValue: any = "Hello, TypeScript!";
let strLength: number = (someValue as string).length;
```

## 🔹 Modules (Import/Export)
```ts
// Export
export function greet(name: string): string {
    return `Hello, ${name}`;
}

// Import
import { greet } from "./module";
```

## 🔹 Utility Types
```ts
type Person = {
    name: string;
    age: number;
};

// Partial: Makes all properties optional
const partialPerson: Partial<Person> = { name: "John" };

// Readonly: Prevents modification
const readonlyPerson: Readonly<Person> = { name: "Jane", age: 30 };
```

## 🔹 Asynchronous Programming
```ts
async function fetchData(): Promise<string> {
    return new Promise((resolve) => {
        setTimeout(() => resolve("Data fetched!"), 1000);
    });
}

fetchData().then(console.log);
```

## 🔹 TypeScript Best Practices
- Prefer `const` and `let` over `var`.
- Use **strict types** to avoid implicit `any`.
- Prefer **interfaces** for object structures.
- Use **readonly** for immutable properties.
- Use **generics** to write reusable functions and components.
- Avoid using `any` unless absolutely necessary.

---