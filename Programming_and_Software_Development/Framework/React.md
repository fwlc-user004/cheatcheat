# React Practical Cheat Sheet

## 📌 Introduction
React is a JavaScript library for building interactive user interfaces using components and state management.

---

## 🚀 Installation & Setup
### Install React via Create React App
```sh
npx create-react-app my-app
cd my-app
npm start
```

### Install React via Vite (Faster Build Tool)
```sh
npm create vite@latest my-app --template react
cd my-app
npm install
npm run dev
```

---

## 🏗️ Project Structure
```plaintext
my-app/
 ├── node_modules/
 ├── public/
 ├── src/
 │   ├── components/
 │   ├── App.js
 │   ├── index.js
 │   ├── styles.css
 ├── .gitignore
 ├── package.json
 ├── README.md
```

---

## 🔹 JSX (JavaScript XML)
```jsx
const element = <h1>Hello, React!</h1>;
```

### JSX Expressions
```jsx
const name = "John";
const element = <h1>Hello, {name}!</h1>;
```

---

## 🔹 Functional Components (Recommended)
```jsx
function Welcome({ name }) {
    return <h1>Welcome, {name}!</h1>;
}
```

### Using a Component
```jsx
function App() {
    return (
        <div>
            <Welcome name="Alice" />
        </div>
    );
}
```

---

## 🔹 State & Hooks
### Using `useState` Hook
```jsx
import { useState } from 'react';

function Counter() {
    const [count, setCount] = useState(0);

    return (
        <div>
            <p>Count: {count}</p>
            <button onClick={() => setCount(count + 1)}>Increment</button>
        </div>
    );
}
```

---

## 🔹 Handling Events
```jsx
function Button() {
    function handleClick() {
        alert("Button Clicked!");
    }
    return <button onClick={handleClick}>Click Me</button>;
}
```

---

## 🔹 Conditional Rendering
```jsx
function Greeting({ isLoggedIn }) {
    return isLoggedIn ? <h1>Welcome Back!</h1> : <h1>Please Sign In</h1>;
}
```

---

## 🔹 Lists & Keys
```jsx
const names = ['Alice', 'Bob', 'Charlie'];
const listItems = names.map((name, index) => <li key={index}>{name}</li>);
```

---

## 🔹 Forms
```jsx
function Form() {
    const [input, setInput] = useState("");
    function handleSubmit(event) {
        event.preventDefault();
        alert(`Submitted: ${input}`);
    }
    return (
        <form onSubmit={handleSubmit}>
            <input type="text" value={input} onChange={(e) => setInput(e.target.value)} />
            <button type="submit">Submit</button>
        </form>
    );
}
```

---

## 🔹 `useEffect` Hook (Side Effects)
```jsx
import { useState, useEffect } from 'react';

function Timer() {
    const [count, setCount] = useState(0);
    useEffect(() => {
        const interval = setInterval(() => {
            setCount(c => c + 1);
        }, 1000);
        return () => clearInterval(interval);
    }, []);
    return <p>Count: {count}</p>;
}
```

---

## 🔹 React Router (Navigation)
### Install React Router
```sh
npm install react-router-dom
```

### Set Up Routing
```jsx
import { BrowserRouter as Router, Route, Routes, Link } from 'react-router-dom';

function Home() {
    return <h1>Home Page</h1>;
}

function About() {
    return <h1>About Page</h1>;
}

function App() {
    return (
        <Router>
            <nav>
                <Link to="/">Home</Link>
                <Link to="/about">About</Link>
            </nav>
            <Routes>
                <Route path="/" element={<Home />} />
                <Route path="/about" element={<About />} />
            </Routes>
        </Router>
    );
}
```

