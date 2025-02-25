# 🚀 Express.js Comprehensive Cheatsheet

## 🔹 Install & Setup
```sh
# Install Express.js
npm install express

# Create an Express app
mkdir myapp && cd myapp
npm init -y
npm install express
```

## 🔹 Basic Express Server
```js
const express = require("express");
const app = express();

app.get("/", (req, res) => {
    res.send("Hello, Express!");
});

app.listen(3000, () => console.log("Server running on port 3000"));
```

## 🔹 Middleware
```js
// Global middleware
app.use(express.json());
app.use(express.urlencoded({ extended: true }));

// Custom middleware
app.use((req, res, next) => {
    console.log(`Request received: ${req.method} ${req.url}`);
    next();
});
```

## 🔹 Routing
```js
app.get("/users", (req, res) => {
    res.json([{ name: "Alice" }, { name: "Bob" }]);
});

app.post("/users", (req, res) => {
    res.send("User created");
});

app.put("/users/:id", (req, res) => {
    res.send(`User ${req.params.id} updated`);
});

app.delete("/users/:id", (req, res) => {
    res.send(`User ${req.params.id} deleted`);
});
```

## 🔹 Route Parameters & Query Strings
```js
app.get("/user/:id", (req, res) => {
    res.send(`User ID: ${req.params.id}`);
});

app.get("/search", (req, res) => {
    res.send(`Search query: ${req.query.q}`);
});
```

## 🔹 Static Files
```js
app.use(express.static("public"));
```

## 🔹 Error Handling
```js
app.use((err, req, res, next) => {
    console.error(err.stack);
    res.status(500).send("Something went wrong!");
});
```

## 🔹 Express Router
```js
const userRouter = express.Router();

userRouter.get("/", (req, res) => {
    res.send("User List");
});

userRouter.post("/", (req, res) => {
    res.send("User Created");
});

app.use("/users", userRouter);
```

## 🔹 CORS (Cross-Origin Resource Sharing)
```sh
npm install cors
```
```js
const cors = require("cors");
app.use(cors());
```

## 🔹 Connecting to MongoDB with Mongoose
```sh
npm install mongoose
```
```js
const mongoose = require("mongoose");

mongoose.connect("mongodb://localhost:27017/mydb", {
    useNewUrlParser: true,
    useUnifiedTopology: true
}).then(() => console.log("Connected to MongoDB"));
```

## 🔹 JSON Web Tokens (JWT) Authentication
```sh
npm install jsonwebtoken
```
```js
const jwt = require("jsonwebtoken");
const secret = "mysecret";

app.post("/login", (req, res) => {
    const token = jwt.sign({ user: "Alice" }, secret, { expiresIn: "1h" });
    res.json({ token });
});
```

## 🔹 Handling File Uploads with Multer
```sh
npm install multer
```
```js
const multer = require("multer");
const upload = multer({ dest: "uploads/" });

app.post("/upload", upload.single("file"), (req, res) => {
    res.send("File uploaded!");
});
```

## 🔹 Rate Limiting
```sh
npm install express-rate-limit
```
```js
const rateLimit = require("express-rate-limit");
const limiter = rateLimit({
    windowMs: 15 * 60 * 1000, // 15 minutes
    max: 100 // Limit each IP to 100 requests per window
});
app.use(limiter);
```

## 🔹 WebSockets with Socket.io
```sh
npm install socket.io
```
```js
const http = require("http");
const socketIo = require("socket.io");
const server = http.createServer(app);
const io = socketIo(server);

io.on("connection", (socket) => {
    console.log("A user connected");
    socket.on("message", (msg) => console.log(msg));
});

server.listen(3000, () => console.log("Server running on port 3000"));
```

## 🔹 Express Best Practices
- Use middleware for modularization.
- Validate request data before processing.
- Use environment variables for sensitive data.
- Optimize database queries to prevent performance bottlenecks.
- Implement proper error handling for better debugging.

---