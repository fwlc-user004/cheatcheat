# 📜 Log Levels Cheat Sheet

## 🛠 What are Log Levels?
Log levels define the **severity** and **importance** of log messages in an application. They help developers monitor, debug, and troubleshoot issues efficiently.

### 🎯 Why Use Log Levels?
✅ Helps in debugging and troubleshooting  
✅ Improves system monitoring and performance analysis  
✅ Prioritizes issues based on severity  
✅ Reduces unnecessary logging overhead  
✅ Enhances security by logging critical events  

---

## 🚦 Common Log Levels Explained

| Level       | Severity | Purpose | When to Use |
|------------|----------|---------|------------|
|🟣**TRACE**| Lowest | Most detailed log level, logs every single step of execution | Debugging deeply nested logic, performance bottlenecks, and function calls |
|🔵**DEBUG**| Low | Provides detailed diagnostic information useful for debugging | Understanding system behavior, diagnosing unexpected outputs |
|🟢**INFO**| Normal | Logs general operational events without problems | Application startup, shutdown, configuration changes, routine operations |
|🟡**WARN**| Medium | Highlights potential issues that might lead to errors | Deprecated API usage, performance warnings, unusual but non-fatal scenarios |
|🔴**ERROR**| High | Captures runtime issues that require immediate attention | API failures, exceptions, database connection issues, failed authentication |
|⚫**FATAL**| Critical | Logs system failures that cause application crashes | System crashes, data loss, unrecoverable errors |

---

## 🔥 Log Level Hierarchy (Least to Most Severe)

```
TRACE → DEBUG → INFO → WARN → ERROR → FATAL
```

- **Lower Levels (TRACE, DEBUG, INFO)** → Used during development for detailed insights.
- **Higher Levels (WARN, ERROR, FATAL)** → Used in production to catch and report critical issues.

---

## 📌 Example Logs for Each Level

```plaintext
[TRACE] Checking database connection step by step...
[DEBUG] User ID 1234 fetched from API.
[INFO] Application started successfully on port 8080.
[WARN] Deprecated method `oldFunction()` used, update recommended.
[ERROR] Payment gateway request failed. Response: 500 Internal Server Error.
[FATAL] Database connection lost! System shutting down.
```

---

## 🔧 Best Practices for Logging

✅ **Use appropriate log levels** – Avoid logging everything at `ERROR` or `DEBUG`.  
✅ **Avoid logging sensitive data** – Never log passwords, API keys, or personal information.  
✅ **Include context information** – Add timestamps, request IDs, user details where needed.  
✅ **Use structured logging** – JSON format helps with parsing and searching logs.  
✅ **Log exceptions properly** – Capture stack traces to make debugging easier.  
✅ **Rotate logs** – Prevent excessive disk space usage with log rotation.  
✅ **Monitor logs in production** – Use tools like **ELK Stack, Splunk, Graylog, Loki, Prometheus**.  

---

## ⚡ Structured Logging (JSON Format Example)
Instead of logging raw text, use structured logs:

```json
{
  "level": "error",
  "timestamp": "2025-02-22T12:34:56Z",
  "message": "Failed to process payment",
  "user_id": 12345,
  "order_id": "ORD56789",
  "error": "TimeoutException"
}
```

**Benefits of structured logging:**  
✔ Easier to search and analyze logs  
✔ Works well with log aggregation tools  
✔ Better performance for large-scale systems  

---

## 🚀 Logging Tools & Frameworks

| Language  | Popular Logging Frameworks |
|-----------|---------------------------|
| **Java**  | Log4j, SLF4J, Logback |
| **Python** | Logging Module, Loguru |
| **JavaScript (Node.js)** | Winston, Bunyan, Pino |
| **C#** | NLog, Serilog |
| **Go** | Logrus, Zap |
| **PHP** | Monolog |
| **Ruby** | Logger |
| **Shell (Linux)** | Syslog, journalctl |

---

## 🔄 Setting Log Levels in Different Languages

### 🟢 Java (Log4j)
```java
import org.apache.log4j.Logger;
Logger logger = Logger.getLogger(MyClass.class);
logger.debug("This is a debug message");
logger.error("This is an error message");
```

### 🟡 Python (Logging Module)
```python
import logging
logging.basicConfig(level=logging.DEBUG)
logging.info("Application started")
logging.warning("This is a warning")
logging.error("This is an error")
```

### 🔴 JavaScript (Winston)
```javascript
const winston = require('winston');
const logger = winston.createLogger({ level: 'info', transports: [new winston.transports.Console()] });
logger.info('App started successfully');
logger.error('Something went wrong');
```

### ⚫ C# (Serilog)
```csharp
using Serilog;
Log.Logger = new LoggerConfiguration().WriteTo.Console().CreateLogger();
Log.Information("App started successfully");
Log.Error("Critical failure detected!");
```

---

## 🚀 Final Thoughts

- **Log what matters** – Avoid excessive or irrelevant logs.  
- **Use the right level** – Keep debugging logs separate from production logs.  
- **Monitor & analyze logs** – Logs are valuable for troubleshooting and security.  

