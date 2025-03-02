# 🚀 JavaScript (ES6+) Cheatsheet

## 🔹 Variables & Constants
```js
let x = 10; // Mutable variable
const y = 20; // Immutable constant
var z = 30; // Avoid using var (function-scoped)
```

## 🔹 Data Types
```js
let num = 42; // Number
let str = "Hello"; // String
let bool = true; // Boolean
let arr = [1, 2, 3]; // Array
let obj = { key: "value" }; // Object
let n = null; // Null
let u = undefined; // Undefined
```

## 🔹 Template Literals
```js
let name = "John";
console.log(`Hello, ${name}!`); // String interpolation
```

## 🔹 Arrow Functions
```js
const add = (a, b) => a + b;
console.log(add(5, 3));
```

## 🔹 Destructuring
```js
// Array Destructuring
let [a, b, c] = [1, 2, 3];

// Object Destructuring
let person = { name: "Alice", age: 25 };
let { name, age } = person;
```

## 🔹 Spread & Rest Operators
```js
// Spread
let arr1 = [1, 2, 3];
let arr2 = [...arr1, 4, 5];

// Rest
const sum = (...numbers) => numbers.reduce((acc, num) => acc + num, 0);
console.log(sum(1, 2, 3, 4));
```

## 🔹 Default Parameters
```js
const greet = (name = "Guest") => `Hello, ${name}!`;
console.log(greet());
```

## 🔹 Object Literals
```js
const createPerson = (name, age) => ({ name, age });
console.log(createPerson("Alice", 30));
```

## 🔹 Promises & Async/Await
```js
const fetchData = async () => {
    try {
        let response = await fetch("https://api.example.com/data");
        let data = await response.json();
        console.log(data);
    } catch (error) {
        console.error("Error fetching data", error);
    }
};
fetchData();
```

## 🔹 Map, Filter, Reduce
```js
let numbers = [1, 2, 3, 4, 5];

// Map
let doubled = numbers.map(n => n * 2);

// Filter
let evens = numbers.filter(n => n % 2 === 0);

// Reduce
let sum = numbers.reduce((acc, n) => acc + n, 0);
```

## 🔹 Modules (Import/Export)
```js
// Export
export const add = (a, b) => a + b;

// Import
import { add } from "./math.js";
```

## 🔹 Classes
```js
class Person {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }
    greet() {
        console.log(`Hello, my name is ${this.name}`);
    }
}
const alice = new Person("Alice", 30);
alice.greet();
```

## 🔹 Higher Order Functions
```js
const operate = (fn, a, b) => fn(a, b);
console.log(operate((x, y) => x * y, 5, 4));
```

## 🔹 Event Listeners
```js
document.querySelector("button").addEventListener("click", () => {
    console.log("Button clicked!");
});
```

## 🔹 Local Storage
```js
localStorage.setItem("key", "value");
console.log(localStorage.getItem("key"));
localStorage.removeItem("key");
```

## 🔹 Set & Map
```js
let uniqueNumbers = new Set([1, 2, 3, 3, 4]);
let users = new Map();
users.set("Alice", 25);
users.set("Bob", 30);
```

## 🔹 Fetch API
```js
fetch("https://api.example.com")
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error("Error fetching data", error));
```

## 🔹 Debounce & Throttle
```js
const debounce = (func, delay) => {
    let timer;
    return (...args) => {
        clearTimeout(timer);
        timer = setTimeout(() => func(...args), delay);
    };
};

const throttle = (func, limit) => {
    let inThrottle;
    return (...args) => {
        if (!inThrottle) {
            func(...args);
            inThrottle = true;
            setTimeout(() => (inThrottle = false), limit);
        }
    };
};
```

## 🔹 ES6+ Best Practices
- Use `const` and `let` instead of `var`.
- Prefer arrow functions for concise syntax.
- Use template literals instead of string concatenation.
- Destructure objects and arrays for cleaner code.
- Use default parameters to handle missing arguments.
- Write modular code with ES6 modules.
- Use `async/await` instead of callback hell.

---