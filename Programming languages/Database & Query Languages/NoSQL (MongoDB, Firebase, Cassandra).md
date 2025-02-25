# 🚀 NoSQL (MongoDB, Firebase, Cassandra) Comprehensive Cheatsheet

## 🔹 MongoDB

### Install & Setup
```sh
# Install MongoDB
sudo apt install mongodb  # Linux
brew install mongodb      # macOS

# Start MongoDB
mongod --dbpath /data/db

# Connect to Mongo Shell
mongo
```

### Basic Commands
```sh
# Show databases
show dbs

# Use or create a database
use my_database

# Show collections
show collections
```

### CRUD Operations
```js
// Insert document
use my_database
db.users.insertOne({ name: "Alice", age: 25 })

// Find documents
db.users.find({ age: { $gt: 20 } })

// Update document
db.users.updateOne({ name: "Alice" }, { $set: { age: 26 } })

// Delete document
db.users.deleteOne({ name: "Alice" })
```

### Indexing for Performance
```js
// Create an index
 db.users.createIndex({ name: 1 })
```

### Aggregation
```js
db.orders.aggregate([
  { $match: { status: "shipped" } },
  { $group: { _id: "$customer_id", total: { $sum: "$amount" } } }
])
```

---

## 🔹 Firebase

### Install & Setup
```sh
# Install Firebase CLI
npm install -g firebase-tools

# Login to Firebase
firebase login

# Initialize Firebase in your project
firebase init
```

### Firestore Database
```js
import { getFirestore, doc, setDoc, getDoc } from "firebase/firestore";

const db = getFirestore();

// Write data
await setDoc(doc(db, "users", "alice"), { name: "Alice", age: 25 });

// Read data
const docSnap = await getDoc(doc(db, "users", "alice"));
if (docSnap.exists()) {
    console.log("Document data:", docSnap.data());
}
```

### Real-time Database
```js
import { getDatabase, ref, set, get } from "firebase/database";

const db = getDatabase();

// Write data
set(ref(db, 'users/alice'), {
  name: "Alice",
  age: 25
});

// Read data
get(ref(db, 'users/alice')).then(snapshot => {
  if (snapshot.exists()) {
    console.log(snapshot.val());
  }
});
```

### Authentication (Email & Password)
```js
import { getAuth, createUserWithEmailAndPassword } from "firebase/auth";

const auth = getAuth();
createUserWithEmailAndPassword(auth, "user@example.com", "password123")
  .then(userCredential => console.log(userCredential.user))
  .catch(error => console.error(error));
```

---

## 🔹 Cassandra

### Install & Setup
```sh
# Install Cassandra
sudo apt install cassandra  # Linux
brew install cassandra      # macOS

# Start Cassandra
cassandra -f

# Connect to CQL shell
cqlsh
```

### Basic Commands
```sql
-- Show keyspaces
DESCRIBE KEYSPACES;

-- Create keyspace
CREATE KEYSPACE my_keyspace WITH replication = {
  'class': 'SimpleStrategy', 'replication_factor': 1
};

-- Use a keyspace
USE my_keyspace;
```

### Create Table
```sql
CREATE TABLE users (
    id UUID PRIMARY KEY,
    name TEXT,
    age INT
);
```

### Insert & Query Data
```sql
-- Insert data
INSERT INTO users (id, name, age) VALUES (uuid(), 'Alice', 25);

-- Select data
SELECT * FROM users WHERE age > 20;
```

### Indexing
```sql
CREATE INDEX ON users (name);
```

---

## 🔹 NoSQL Best Practices
- **Use indexing** to optimize query performance.
- **Denormalize data** where necessary to reduce query complexity.
- **Use batch operations** to minimize network requests.
- **Implement security rules** in Firebase to protect data.
- **Optimize query structures** for scalability in Cassandra.

---