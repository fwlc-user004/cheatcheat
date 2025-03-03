# 🌍 Subnetting & IPv4/IPv6 Comprehensive Cheatsheet

## 🔹 Introduction
Subnetting is the process of dividing a **network into smaller subnetworks (subnets)** to improve routing efficiency and network security.

---

## 🔹 IPv4 Addressing
### ✅ Structure
- **32-bit address** divided into **4 octets** (e.g., `192.168.1.1`).
- **Each octet** is **8 bits** (range: `0 - 255`).

### 📌 IPv4 Classes
| Class | Range            | Default Subnet Mask |
|-------|----------------|------------------|
| A     | 1.0.0.0 - 126.255.255.255 | 255.0.0.0 ( /8 ) |
| B     | 128.0.0.0 - 191.255.255.255 | 255.255.0.0 ( /16 ) |
| C     | 192.0.0.0 - 223.255.255.255 | 255.255.255.0 ( /24 ) |
| D     | 224.0.0.0 - 239.255.255.255 | Multicast |
| E     | 240.0.0.0 - 255.255.255.255 | Reserved |

### 📌 Private IPv4 Ranges
| Class | Range |
|-------|----------------|
| A     | 10.0.0.0 - 10.255.255.255 |
| B     | 172.16.0.0 - 172.31.255.255 |
| C     | 192.168.0.0 - 192.168.255.255 |

---

## 🔹 Subnetting
### ✅ CIDR Notation
- Instead of using **classful addressing**, we use **CIDR (Classless Inter-Domain Routing)**.
- **Example:** `192.168.1.0/24` → `/24` means **first 24 bits are the network, remaining 8 bits are hosts**.

### 📌 Subnet Mask to CIDR Table
| CIDR | Subnet Mask | Hosts Per Subnet |
|------|------------|------------------|
| /8   | 255.0.0.0  | 16,777,214 |
| /16  | 255.255.0.0 | 65,534 |
| /24  | 255.255.255.0 | 254 |
| /30  | 255.255.255.252 | 2 |

### 📌 Subnetting Example
- **Given Network:** `192.168.1.0/24`
- **Divide into 4 subnets:** `/26` (Subnet Mask: `255.255.255.192`)
- **New Subnets:**
  - `192.168.1.0/26` (64 hosts)
  - `192.168.1.64/26`
  - `192.168.1.128/26`
  - `192.168.1.192/26`

---

## 🔹 IPv6 Addressing
### ✅ Structure
- **128-bit address** written in hexadecimal (e.g., `2001:0db8:85a3::8a2e:0370:7334`).
- **Divided into 8 blocks**, separated by `:`.

### 📌 Types of IPv6 Addresses
| Type            | Example            | Purpose |
|----------------|------------------|------------|
| Unicast       | `2001:db8::1`     | Single device |
| Multicast     | `ff02::1`         | Multiple devices |
| Link-local    | `fe80::1`         | Auto-assigned, non-routable |
| Global Unicast | `2001::/16`      | Public internet |

### 📌 IPv6 Address Shortening Rules
- Remove **leading zeros** → `2001:0db8:0000:0000:0000:0000:0000:1` → `2001:db8::1`
- Use **`::` for consecutive zeros** → `fe80:0000:0000:0000:abcd:1234:5678:90ab` → `fe80::abcd:1234:5678:90ab`

---

## 🔹 Key Differences: IPv4 vs IPv6
| Feature         | IPv4                  | IPv6                  |
|---------------|---------------------|---------------------|
| Address Size  | 32-bit               | 128-bit            |
| Address Format | Decimal (e.g., `192.168.1.1`) | Hexadecimal (e.g., `2001:db8::1`) |
| Total Addresses | 4.3 billion         | 340 undecillion    |
| NAT Required  | Yes                  | No                 |
| Security      | Optional (IPSec)      | Built-in (IPSec)   |

---

## 🔹 Networking Commands
```sh
# Show IP configuration (Linux/macOS)
ip a

# Show IP configuration (Windows)
ipconfig /all

# Test connectivity (IPv4 & IPv6)
ping 8.8.8.8
ping -6 google.com

# Trace route to a host
traceroute example.com   # Linux/macOS
tracert example.com      # Windows
```

---

## 🔹 Subnetting & IPv6 Best Practices
- **Use CIDR** to create efficient subnets.
- **Avoid using classful networks** (Class A, B, C) for flexibility.
- **Implement IPv6 early** to future-proof networks.
- **Use link-local IPv6 addresses** for local communication.
- **Ensure proper subnetting** to prevent IP exhaustion.

---