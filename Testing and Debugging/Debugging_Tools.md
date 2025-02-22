# 🛠 Debugging Tools Cheat Sheet

## 🔍 What is Debugging?
Debugging is the process of identifying, analyzing, and fixing bugs (errors) in software.

---

## 🚀 Common Debugging Tools & Techniques

| Tool             | Type               | Features |
|-----------------|-------------------|----------|
| **Chrome DevTools** | Browser Debugging | Inspect elements, network requests, JavaScript debugging |
| **Firebug (Firefox DevTools)** | Browser Debugging | Inspect and modify HTML, CSS, JS |
| **Visual Studio Debugger** | IDE Debugging | Step through code, breakpoints, watches |
| **GDB (GNU Debugger)** | C/C++ Debugging | Command-line debugging, breakpoints, memory inspection |
| **LLDB** | macOS Debugging | Alternative to GDB for macOS/iOS development |
| **Xcode Debugger** | iOS/macOS Debugging | Visual debugging, memory analysis |
| **Android Studio Debugger** | Android Debugging | Logcat, step-through debugging, emulator testing |
| **PyCharm Debugger** | Python Debugging | Breakpoints, watches, step execution |
| **PDB (Python Debugger)** | Python Debugging | CLI debugging, breakpoints (`import pdb`) |
| **WinDbg** | Windows Debugging | Kernel and application debugging |
| **Eclipse Debugger** | Java Debugging | Step execution, breakpoints, expressions |
| **Postman** | API Debugging | Test and debug REST APIs |
| **Wireshark** | Network Debugging | Packet sniffing, network traffic analysis |
| **Fiddler** | HTTP Debugging | Captures and analyzes HTTP requests |
| **Sentry** | Error Monitoring | Real-time error tracking for web and mobile apps |

---

## 🛠 Debugging Strategies

### 🐞 1. **Reproduce the Bug**
- Find a consistent way to trigger the bug.
- Document inputs, outputs, and expected behavior.

### 🎯 2. **Use Logging & Tracing**
- **Console Logging:**
  - JavaScript: `console.log("Debug Info")`
  - Python: `print("Debug Info")`
  - Java: `System.out.println("Debug Info")`
- **Advanced Logging:**
  - Use log levels (INFO, DEBUG, ERROR)
  - Log to files instead of cluttering the console
  - Tools: Log4j (Java), Winston (Node.js), Python Logging module

### ⏸ 3. **Use Breakpoints**
- Pause execution at specific lines
- Inspect variable values at runtime
- Step through code line by line

### 🔍 4. **Check Error Messages**
- Read stack traces carefully
- Identify the source of the error
- Search online for solutions

### 🛠 5. **Use Debugging Tools**
- **IDE Debuggers** for real-time inspection
- **Network Tools** for API and HTTP debugging
- **Memory Profilers** for detecting leaks

### 🚀 6. **Binary Search Debugging**
- Use `print()` statements or breakpoints to narrow down the problem.

### 🧪 7. **Test with Edge Cases**
- Try different inputs (valid, invalid, boundary values).
- Check for unexpected behavior.

### ⚙️ 8. **Check Dependencies**
- Verify versions of libraries and frameworks.
- Ensure all dependencies are installed correctly.

### 🔄 9. **Rollback to Previous Versions**
- Identify when the bug was introduced using **Git bisect**.

---

## 📌 Common Debugging Mistakes
❌ Ignoring error messages  
❌ Skipping logs and stack traces  
❌ Making multiple changes at once  
❌ Debugging in production without testing first  
❌ Forgetting to remove debug logs before deployment  

---

## 🔥 Pro Debugging Tips
✅ Keep code modular and easy to debug  
✅ Use meaningful log messages  
✅ Automate testing to catch issues early  
✅ Use remote debugging for production environments  
✅ Document common issues and their fixes  

---

🚀 **Debug Smart, Code Better!** 🛠

