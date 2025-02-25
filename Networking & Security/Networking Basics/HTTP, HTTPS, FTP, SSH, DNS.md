# 🌍 HTTP, HTTPS, FTP, SSH, DNS Comprehensive Cheatsheet

## 🔹 Introduction
These are the most commonly used network protocols for web communication, file transfer, remote access, and domain resolution.

---

## 🔹 HTTP (HyperText Transfer Protocol)
### ✅ Overview
- Used for **communication between web browsers and servers**.
- **Stateless and unencrypted**.
- Works on **port 80**.

### 📌 Common HTTP Methods
| Method  | Description  |
|---------|-------------|
| GET     | Retrieve data |
| POST    | Submit data |
| PUT     | Update data |
| DELETE  | Remove data |

### 📌 Example HTTP Request
```http
GET /index.html HTTP/1.1
Host: example.com
User-Agent: Mozilla/5.0
```

### 📌 Example HTTP Response
```http
HTTP/1.1 200 OK
Content-Type: text/html

<html><body>Hello, World!</body></html>
```

---

## 🔹 HTTPS (HTTP Secure)
### ✅ Overview
- **Secure version of HTTP** using **SSL/TLS encryption**.
- Prevents **man-in-the-middle (MITM) attacks**.
- Works on **port 443**.

### 📌 How to Check HTTPS Certificate
```sh
openssl s_client -connect example.com:443
```

---

## 🔹 FTP (File Transfer Protocol)
### ✅ Overview
- Used for **transferring files between client and server**.
- **Unencrypted**, use **FTPS or SFTP** for security.
- Works on **ports 20 & 21**.

### 📌 Common FTP Commands
```sh
ftp ftp.example.com   # Connect to an FTP server
ls                    # List files
get filename          # Download file
put filename          # Upload file
bye                   # Exit FTP session
```

---

## 🔹 SSH (Secure Shell)
### ✅ Overview
- Used for **secure remote login** and command execution.
- Uses **strong encryption** (RSA, AES, etc.).
- Works on **port 22**.

### 📌 SSH Commands
```sh
# Connect to a remote server
ssh user@example.com

# Copy files securely
scp file.txt user@example.com:/home/user/

# Generate SSH key pair
ssh-keygen -t rsa -b 4096
```

---

## 🔹 DNS (Domain Name System)
### ✅ Overview
- Resolves **domain names to IP addresses**.
- Uses **port 53**.
- Hierarchical structure: **Root → TLD → Domain**.

### 📌 Check DNS Records
```sh
nslookup example.com

# Get detailed DNS records
dig example.com ANY

# Flush DNS cache
sudo systemd-resolve --flush-caches  # Linux
ipconfig /flushdns  # Windows
```

---

## 🔹 Best Practices
- **Use HTTPS** instead of HTTP for security.
- **Enable SSH key authentication** instead of passwords.
- **Use SFTP/FTPS** instead of plain FTP.
- **Use DNSSEC** to prevent spoofing and attacks.

---
