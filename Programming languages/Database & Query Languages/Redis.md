# 🚀 Redis Comprehensive Cheatsheet

## 🔹 Install & Setup
```sh
# Install Redis (Linux/macOS)
sudo apt install redis  # Ubuntu/Debian
brew install redis      # macOS

# Start Redis Server
redis-server

# Connect to Redis CLI
redis-cli
```

## 🔹 Basic Commands
```sh
# Ping Redis Server
PING  # Output: PONG

# Set and Get a Key-Value Pair
SET name "Alice"
GET name  # Output: Alice

# Delete a Key
DEL name

# Check if Key Exists
EXISTS name  # Output: 1 (exists) or 0 (doesn't exist)
```

## 🔹 Expiring Keys
```sh
# Set key with expiration (seconds)
SETEX session 60 "Active"

# Set expiration time for existing key
EXPIRE name 30

# Get remaining time to live (TTL)
TTL session
```

## 🔹 Lists (Ordered Collections)
```sh
# Push elements into a list
LPUSH tasks "Task1" "Task2"
RPUSH tasks "Task3"

# Get elements from a list
LRANGE tasks 0 -1  # Get all elements

# Pop element from list
LPOP tasks  # Remove first element
RPOP tasks  # Remove last element
```

## 🔹 Sets (Unique Unordered Collections)
```sh
# Add elements to a set
SADD users "Alice" "Bob" "Charlie"

# Get all elements from a set
SMEMBERS users

# Check if element exists in set
SISMEMBER users "Alice"  # Output: 1 (exists) or 0 (not exists)

# Remove element from set
SREM users "Alice"
```

## 🔹 Hashes (Key-Value Pairs)
```sh
# Set key-value pairs inside a hash
HSET user:1 name "Alice" age "25"

# Get all fields from a hash
HGETALL user:1

# Get specific field value
HGET user:1 name

# Delete a field from hash
HDEL user:1 age
```

## 🔹 Sorted Sets (Unique + Score-Based Ordering)
```sh
# Add elements with scores
ZADD leaderboard 100 "Alice" 200 "Bob"

# Get elements sorted by score
ZRANGE leaderboard 0 -1 WITHSCORES

# Remove an element from sorted set
ZREM leaderboard "Alice"
```

## 🔹 Transactions
```sh
MULTI  # Start transaction
SET key1 "value1"
SET key2 "value2"
EXEC  # Execute transaction
```

## 🔹 Pub/Sub (Publish-Subscribe)
```sh
# Subscribe to a channel
SUBSCRIBE news

# Publish a message to channel
PUBLISH news "Breaking News!"
```

## 🔹 Persistence
```sh
# Save data to disk (snapshot)
SAVE  # Synchronous
BGSAVE  # Asynchronous

# Get last save timestamp
LASTSAVE
```

## 🔹 Connection & Configuration
```sh
# Get Redis configuration
CONFIG GET *

# Set a configuration dynamically
CONFIG SET maxmemory 100mb
```

## 🔹 Redis with Node.js
```js
const redis = require("redis");
const client = redis.createClient();

client.on("connect", () => {
    console.log("Connected to Redis");
});

// Set a key
client.set("name", "Alice", redis.print);

// Get a key
client.get("name", (err, reply) => {
    console.log(reply);
});
```

## 🔹 Redis Best Practices
- Use **keys with namespaces** (`user:123:profile`) to organize data.
- **Avoid large keys** and **use expiration** for cache management.
- Use **pipelines** for batch operations to improve performance.
- Optimize **memory usage** with `LRU` (Least Recently Used) eviction policies.

---