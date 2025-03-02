# 🌐 Network Security & Scanning Cheatsheet

## 🔹 Introduction
Network security involves **identifying vulnerabilities** and **analyzing network traffic** to prevent unauthorized access and attacks. Network scanning helps map network structures and discover potential security risks.

---

## 🔹 Types of Network Scanning
| Scan Type | Purpose |
|-----------|---------|
| **Port Scanning** | Identifies open ports and services running on a target |
| **Service & Version Detection** | Determines software running on open ports |
| **Vulnerability Scanning** | Identifies known security flaws in services |
| **Live Host Discovery** | Finds active devices on a network |
| **Firewall & IDS Evasion** | Bypasses security defenses to test resilience |

---

## 🔹 Network Scanning with Nmap
### ✅ Basic Host Discovery
```sh
nmap -sn 192.168.1.0/24  # Ping scan (list active hosts)
```

### ✅ Port Scanning
```sh
nmap -p 80,443 192.168.1.1  # Scan specific ports
nmap -p- 192.168.1.1  # Scan all 65,535 ports
```

### ✅ Service & Version Detection
```sh
nmap -sV 192.168.1.1  # Detect service versions
```

### ✅ OS Detection
```sh
nmap -O 192.168.1.1  # Detect operating system
```

### ✅ Aggressive Scan (OS, Services, Scripts)
```sh
nmap -A 192.168.1.1
```

---

## 🔹 Enumerating Open Ports & Services
### ✅ Banner Grabbing (Detect Running Services)
```sh
nc -v 192.168.1.1 22  # Check SSH service banner
```
```sh
telnet 192.168.1.1 80  # Check web server response
```

### ✅ Identify Network Shares (SMB, FTP, SNMP)
```sh
nmap --script=smb-os-discovery 192.168.1.1
```
```sh
nmap --script=ftp-anon 192.168.1.1  # Check anonymous FTP access
```

---

## 🔹 Firewall & IDS Evasion Techniques
### ✅ Slow Scanning to Avoid Detection
```sh
nmap -T2 192.168.1.1  # Slow scan to evade IDS
```

### ✅ Spoof Source IP
```sh
nmap -S 192.168.1.100 192.168.1.1  # Fake source IP
```

### ✅ Scan from a Decoy IP
```sh
nmap -D RND:10 192.168.1.1  # Use 10 decoy IPs
```

---

## 🔹 Network Traffic Analysis
### ✅ Packet Sniffing with Wireshark
- **Capture live traffic:** Select network interface and start capture.
- **Apply filters:**
  - `ip.addr == 192.168.1.1` → Show traffic for a specific IP
  - `tcp.port == 80` → Show HTTP traffic
  - `udp.port == 53` → Show DNS requests

### ✅ Packet Sniffing with Tcpdump
```sh
tcpdump -i eth0 -nn port 80  # Capture HTTP traffic
```
```sh
tcpdump -i eth0 -X port 53  # Capture DNS queries
```

---

## 🔹 Best Practices
- **Use network scanning legally** and only with permission.
- **Combine passive & active reconnaissance** for better results.
- **Avoid detection with stealth scanning techniques.**
- **Analyze firewall rules** before testing network security.
- **Use automated scanning tools** (Nmap, Nessus, OpenVAS) for vulnerability detection.

---