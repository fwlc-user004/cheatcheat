# 🎮 Ethical Hacking Labs & CTFs Cheatsheet

## 🔹 Introduction
Ethical hacking labs and Capture The Flag (CTF) challenges provide **hands-on cybersecurity training**, allowing hackers to practice exploiting vulnerabilities in a controlled environment.

---

## **🔹 CTF Types & Challenges**
| CTF Type | Description |
|----------|-------------|
| **Jeopardy-Style CTFs** | Solve individual challenges (Web, Crypto, Reverse Engineering) |
| **Attack-Defense CTFs** | Teams attack & defend live systems in real-time |
| **Red Team vs. Blue Team** | Offensive vs. Defensive security simulations |
| **Boot2Root Labs** | Simulated hacking challenges leading to root access |

---

## **🔹 Popular Ethical Hacking Labs & Platforms**
### ✅ Online CTF Platforms
#### 📌 Hack The Box (HTB)
- **Realistic hacking challenges** & active community
- Web, Network, Privilege Escalation, Active Directory labs
- **Command to connect HTB machines:**
```sh
openvpn htb.ovpn
```

#### 📌 TryHackMe (THM)
- Beginner-friendly with guided learning paths
- **CTF rooms for Web, Forensics, Privilege Escalation**

#### 📌 OverTheWire (OTW)
- **Wargames for Linux hacking & privilege escalation**
- Popular challenges: Bandit, Narnia, Leviathan

#### 📌 PicoCTF
- Beginner-friendly CTF hosted by Carnegie Mellon
- Focus on **binary exploitation, web security, cryptography**

---

### ✅ Self-Hosted CTF Labs
#### 📌 VulnHub
- Downloadable vulnerable VMs for **offline penetration testing**
- **Setup:**
```sh
VBoxManage import vulnerable_vm.ova
```

#### 📌 PentesterLab
- Hands-on **web app security & exploitation challenges**
- Focus on **SQLi, XSS, SSRF, IDOR, and API hacking**

#### 📌 CTFd (Capture The Flag Framework)
- **Build your own CTF competitions**
- Install with Docker:
```sh
docker run -p 8000:8000 -d ctfd/ctfd
```

---

## **🔹 Essential CTF Tools & Commands**
### ✅ Web Exploitation
- **Burp Suite** (Intercept HTTP Requests, Modify Headers)
- **SQLMap** (Automated SQL Injection Testing)
```sh
sqlmap -u "http://target.com?id=1" --dbs
```

### ✅ Reverse Engineering
- **Ghidra / IDA Pro** (Disassemblers)
- **Radare2** (Binary analysis)
```sh
r2 -A binary_file
```

### ✅ Cryptography Challenges
- **CyberChef** (Decode/encode various formats)
- **John the Ripper / Hashcat** (Password cracking)
```sh
hashcat -m 0 -a 0 hashes.txt rockyou.txt
```

### ✅ OSINT & Reconnaissance
- **Google Dorking** (Find sensitive information via search engines)
```sh
site:example.com filetype:pdf "confidential"
```
- **theHarvester** (Collect emails, subdomains, and hosts)
```sh
theHarvester -d example.com -l 100 -b google
```

---

## **🔹 Best Practices**
- **Start with beginner-friendly CTFs** before attempting advanced challenges.
- **Use a virtual machine (VM)** for security when testing exploits.
- **Document your process** and take notes for future reference.
- **Join security communities** (HTB, THM Discord, DEFCON groups) to learn from others.

---