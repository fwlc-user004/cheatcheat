# 🔥 Firewalls & Intrusion Detection Comprehensive Cheatsheet

## 🔹 Introduction
Firewalls and Intrusion Detection Systems (**IDS**) are critical components of network security. Firewalls **filter traffic**, while IDS **monitor and alert on malicious activity**.

---

## 🔹 Firewalls
### ✅ What is a Firewall?
- A firewall **controls incoming and outgoing network traffic** based on security rules.
- Can be **hardware-based, software-based, or cloud-based**.
- Operates on **OSI Layer 3 (Network) & Layer 4 (Transport)**.

### 📌 Types of Firewalls
| Firewall Type        | Description |
|----------------------|-------------|
| Packet Filtering    | Filters packets based on source/destination IP, port, protocol. |
| Stateful Inspection | Tracks active connections and allows only expected packets. |
| Proxy Firewall     | Intermediary between clients and servers, filters traffic at application level. |
| Next-Gen Firewall  | Uses deep packet inspection (DPI) and threat intelligence. |

### 📌 Common Firewall Commands
#### **Linux iptables**
```sh
# Allow incoming SSH
sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT

# Block all incoming traffic
sudo iptables -P INPUT DROP
```
#### **Windows Firewall**
```sh
# Allow an application
netsh advfirewall firewall add rule name="AllowApp" dir=in action=allow program="C:\Program Files\App.exe" enable=yes

# Block a port
netsh advfirewall firewall add rule name="BlockPort" dir=in action=block protocol=TCP localport=445
```

---

## 🔹 Intrusion Detection Systems (IDS)
### ✅ What is an IDS?
- **Monitors network traffic** for suspicious activity.
- **Alerts administrators** of potential security breaches.
- **Does NOT actively block traffic** (unless combined with an Intrusion Prevention System - IPS).

### 📌 Types of IDS
| IDS Type           | Description |
|-------------------|-------------|
| Network IDS (NIDS) | Monitors network traffic for malicious patterns. |
| Host-based IDS (HIDS) | Runs on individual hosts, detects unauthorized changes. |
| Hybrid IDS | Combines NIDS & HIDS for better security coverage. |

### 📌 Popular IDS Tools
| Tool | Type |
|------|------|
| **Snort** | Network IDS |
| **Suricata** | Network IDS |
| **OSSEC** | Host-based IDS |
| **Zeek (Bro)** | Network IDS |

### 📌 Snort IDS Example
```sh
# Run Snort in IDS mode
snort -c /etc/snort/snort.conf -A console -i eth0
```

---

## 🔹 Best Practices
- **Use a layered approach** (Firewall + IDS + IPS).
- **Regularly update firewall rules** to adapt to new threats.
- **Monitor IDS logs and alerts** to detect threats early.
- **Use anomaly detection** to identify zero-day attacks.
- **Implement access control policies** to limit exposure.

---