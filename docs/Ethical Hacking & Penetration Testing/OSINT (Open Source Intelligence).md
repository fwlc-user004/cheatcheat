# 🔍 OSINT (Open Source Intelligence) Comprehensive Cheatsheet

## 🔹 Introduction
OSINT (**Open Source Intelligence**) refers to **gathering and analyzing publicly available information** to uncover insights for cybersecurity, investigations, and threat intelligence.

---

## 🔹 OSINT Data Sources
| Category | Examples |
|----------|----------|
| **Search Engines** | Google Dorking, Bing, DuckDuckGo |
| **Social Media** | Facebook, Twitter, LinkedIn, Instagram |
| **WHOIS & DNS** | whois lookup, nslookup, dig, Shodan |
| **Public Records** | Government databases, leaked credentials |
| **Dark Web** | Tor sites, pastebin, dark web marketplaces |

---

## 🔹 Google Dorking (Advanced Search Techniques)
### ✅ Find indexed PDFs
```sh
site:example.com filetype:pdf
```

### ✅ Search for login pages
```sh
inurl:login OR inurl:admin
```

### ✅ Exposed sensitive files
```sh
intitle:"Index of" "passwords.txt"
```

---

## 🔹 WHOIS & DNS Reconnaissance
### ✅ Get WHOIS information
```sh
whois example.com
```

### ✅ Find domain records
```sh
dig example.com any
nslookup -type=ANY example.com
```

---

## 🔹 Social Media OSINT
### ✅ Search Twitter for specific keywords
```sh
site:twitter.com "cyber attack"
```

### ✅ Extract LinkedIn employee lists
```sh
site:linkedin.com company "Target Company"
```

### ✅ Find Instagram profiles
```sh
site:instagram.com "target username"
```

---

## 🔹 OSINT Tools
| Tool | Description |
|------|-------------|
| **Shodan** | Finds exposed devices & services |
| **Maltego** | Visual link analysis for OSINT |
| **theHarvester** | Collects emails, subdomains, and hosts |
| **Recon-ng** | Framework for automated OSINT collection |
| **SpiderFoot** | Automates OSINT intelligence gathering |
| **Wayback Machine** | Retrieves historical website snapshots |

---

## 🔹 OSINT for Cybersecurity & Threat Intelligence
- **Identify exposed credentials** (e.g., Have I Been Pwned API)
- **Detect leaked corporate documents** (Google Dorking, Pastebin search)
- **Track threat actors** (Dark web monitoring, social media intelligence)
- **Monitor phishing domains** (Typosquatting analysis)

---

## 🔹 Best Practices
- **Use multiple OSINT tools** to cross-verify findings.
- **Stay anonymous** (use VPNs, Tor, or burner accounts).
- **Respect privacy & legal boundaries** (always follow ethical hacking principles).
- **Automate OSINT collection** using scripts and tools like Recon-ng.

---
