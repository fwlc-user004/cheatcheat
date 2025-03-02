# JavaScript Cheat Sheet

## Basics

### Output
```javascript
console.log("Hello, JavaScript!"); // Print to console
alert("Hello!");                 // Display an alert dialog
```

### Comments
- Single-line: `// This is a comment`
- Multi-line:
  ```javascript
  /*
   This is a multi-line comment
  */
  ```

### Variables
- Declaring variables:
  ```javascript
  let name = "John";    // Mutable variable
  const PI = 3.14159;    // Constant
  var age = 25;          // Global/function-scoped (legacy)
  ```

## Data Types

### Primitives
- **String:** `'Hello'` or `"Hello"`
- **Number:** `42` or `3.14`
- **Boolean:** `true` or `false`
- **Undefined:** A declared variable without a value
- **Null:** A variable explicitly set to `null`
- **Symbol:** Unique and immutable
- **BigInt:** Large integers, e.g., `123n`

### Objects
- **Object:** Key-value pairs
  ```javascript
  let person = { name: "Alice", age: 30 };
  console.log(person.name);
  ```
- **Array:** Ordered list of elements
  ```javascript
  let colors = ["red", "green", "blue"];
  console.log(colors[0]);
  ```
- **Function:**
  ```javascript
  function greet(name) {
    return `Hello, ${name}!`;
  }
  console.log(greet("Alice"));
  ```

## Operators

### Arithmetic Operators
```javascript
let sum = 5 + 3;       // Addition
let difference = 5 - 3; // Subtraction
let product = 5 * 3;    // Multiplication
let quotient = 5 / 3;   // Division
let remainder = 5 % 3;  // Modulus
let power = 5 ** 3;     // Exponentiation
```

### Comparison Operators
```javascript
5 === "5";  // Strict equality (false)
5 == "5";   // Loose equality (true)
5 !== 3;     // Strict inequality (true)
```

### Logical Operators
```javascript
true && false; // AND (false)
true || false; // OR (true)
!true;         // NOT (false)
```

## Control Flow

### If/Else
```javascript
if (condition) {
  // Code if condition is true
} else if (anotherCondition) {
  // Code for another condition
} else {
  // Code if all conditions are false
}
```

### Switch
```javascript
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
```javascript
for (let i = 0; i < 10; i++) {
  console.log(i);
}
```

### While Loop
```javascript
while (condition) {
  // Code to execute
}
```

### Do-While Loop
```javascript
do {
  // Code to execute
} while (condition);
```

### For-Each Loop (Array)
```javascript
[1, 2, 3].forEach(num => console.log(num));
```

## Functions

### Function Declaration
```javascript
function add(a, b) {
  return a + b;
}
```

### Function Expression
```javascript
const multiply = function(a, b) {
  return a * b;
};
```

### Arrow Functions
```javascript
const greet = name => `Hello, ${name}!`;
```

## Objects

### Create and Access Properties
```javascript
let person = {
  name: "Alice",
  age: 30,
  greet() {
    console.log(`Hello, I am ${this.name}`);
  }
};
console.log(person.name);  // Access property
person.greet();            // Call method
```

### Add or Remove Properties
```javascript
person.job = "Engineer"; // Add property
delete person.age;        // Remove property
```

## Arrays

### Common Methods
```javascript
let fruits = ["apple", "banana", "cherry"];
fruits.push("date");        // Add to end
fruits.pop();                // Remove from end
fruits.shift();              // Remove from start
fruits.unshift("kiwi");     // Add to start
console.log(fruits.includes("banana")); // Check existence
```

## Promises

### Basic Example
```javascript
const promise = new Promise((resolve, reject) => {
  if (success) {
    resolve("Success!");
  } else {
    reject("Failure!");
  }
});

promise
  .then(result => console.log(result))
  .catch(error => console.error(error));
```

## Async/Await

```javascript
async function fetchData() {
  try {
    const response = await fetch("https://api.example.com/data");
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.error(error);
  }
}
```

## Modules

### Export and Import
```javascript
// Export
export const add = (a, b) => a + b;

// Import
import { add } from "./math.js";
```

## Error Handling

### Try-Catch
```javascript
try {
  let result = riskyOperation();
} catch (error) {
  console.error("Error occurred:", error);
}
```

## Debugging

### Use Console
```javascript
console.log("Debugging info");
```

### Breakpoints
- Use browser DevTools to set breakpoints and inspect code.

## Best Practices
- Use `let` and `const` instead of `var`.
- Write modular, reusable code.
- Follow naming conventions: camelCase for variables and functions.
- Use strict equality (`===`) for comparisons.



