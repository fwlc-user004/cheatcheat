# 🚀 Node.js Comprehensive Cheatsheet

## 🔹 Install & Setup
```sh
# Install Node.js (Check https://nodejs.org/ for latest version)
npm install -g node

# Check installed version
node -v

# Initialize a new Node.js project
npm init -y
```

## 🔹 Running a Script
```sh
node script.js
```

## 🔹 Global Objects
```js
console.log(__dirname); // Current directory path
console.log(__filename); // Current file path
```

## 🔹 Importing & Exporting Modules
### CommonJS (Default in Node.js)
```js
// Export
module.exports = {
    greet: function() {
        return "Hello from Node.js!";
    }
};

// Import
const utils = require("./utils");
console.log(utils.greet());
```

### ES6 Modules (Requires package.json "type": "module")
```js
// Export
export const greet = () => "Hello from Node.js!";

// Import
import { greet } from "./utils.js";
console.log(greet());
```

## 🔹 File System (fs Module)
```js
const fs = require("fs");

// Read file
fs.readFile("file.txt", "utf8", (err, data) => {
    if (err) throw err;
    console.log(data);
});

// Write file
fs.writeFile("file.txt", "Hello, Node.js!", (err) => {
    if (err) throw err;
    console.log("File written successfully");
});
```

## 🔹 HTTP Server
```js
const http = require("http");

const server = http.createServer((req, res) => {
    res.writeHead(200, { "Content-Type": "text/plain" });
    res.end("Hello, World!");
});

server.listen(3000, () => console.log("Server running on port 3000"));
```

## 🔹 Express.js Basics
```js
const express = require("express");
const app = express();

app.get("/", (req, res) => {
    res.send("Hello, Express!");
});

app.listen(3000, () => console.log("Server running on port 3000"));
```

## 🔹 Middleware in Express
```js
app.use((req, res, next) => {
    console.log("Middleware executed");
    next();
});
```

## 🔹 Working with JSON
```js
app.use(express.json());
app.post("/data", (req, res) => {
    console.log(req.body);
    res.send("Data received");
});
```

## 🔹 Working with Environment Variables
```sh
# Install dotenv
npm install dotenv
```
```js
require("dotenv").config();
console.log(process.env.API_KEY);
```

## 🔹 Working with Databases (MongoDB + Mongoose)
```sh
# Install Mongoose
npm install mongoose
```
```js
const mongoose = require("mongoose");

mongoose.connect("mongodb://localhost:27017/mydb", {
    useNewUrlParser: true,
    useUnifiedTopology: true
}).then(() => console.log("Connected to MongoDB"));

const UserSchema = new mongoose.Schema({
    name: String,
    age: Number
});

const User = mongoose.model("User", UserSchema);

// Create a user
const newUser = new User({ name: "John", age: 30 });
newUser.save().then(() => console.log("User saved"));
```

## 🔹 Handling Errors
```js
app.use((err, req, res, next) => {
    console.error(err.stack);
    res.status(500).send("Something went wrong!");
});
```

## 🔹 Asynchronous Programming with Promises
```js
const fetchData = () => {
    return new Promise((resolve, reject) => {
        setTimeout(() => resolve("Data fetched!"), 1000);
    });
};

fetchData().then(console.log);
```

## 🔹 Asynchronous Programming with Async/Await
```js
const asyncFunction = async () => {
    try {
        let data = await fetchData();
        console.log(data);
    } catch (error) {
        console.error(error);
    }
};

asyncFunction();
```

## 🔹 WebSockets with Socket.io
```sh
npm install socket.io
```
```js
const io = require("socket.io")(3000);
io.on("connection", (socket) => {
    console.log("A user connected");
    socket.on("message", (msg) => console.log(msg));
});
```

## 🔹 Node.js Best Practices
- Always handle errors with `try...catch` or `.catch()`.
- Use `async/await` for cleaner asynchronous code.
- Store sensitive data in environment variables.
- Validate user input before using it.
- Optimize database queries for performance.
- Use middleware in Express to modularize code.

---