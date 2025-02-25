# 🌐 OSI Model & TCP/IP Comprehensive Cheatsheet

## 🔹 Introduction
The **OSI Model** (Open Systems Interconnection) and **TCP/IP Model** define network communication layers, allowing systems to communicate over the internet and local networks.

---

## 🔹 OSI Model (7 Layers)
### ✅ Overview
| Layer | Name                   | Function |
|-------|------------------------|----------|
| 7     | **Application**         | User interface (HTTP, FTP, SMTP) |
| 6     | **Presentation**        | Data encryption, compression (SSL, TLS) |
| 5     | **Session**             | Manages connections (NetBIOS, RPC) |
| 4     | **Transport**           | Ensures end-to-end communication (TCP, UDP) |
| 3     | **Network**             | Routing and addressing (IP, ICMP) |
| 2     | **Data Link**           | MAC addresses, framing (Ethernet, Wi-Fi) |
| 1     | **Physical**            | Hardware, cables, signals (Ethernet cables, radio waves) |

### 📌 OSI Model Example (Web Browsing)
1. **Application Layer** → User types `https://example.com`
2. **Presentation Layer** → TLS encrypts the HTTP request
3. **Session Layer** → A TCP connection is established
4. **Transport Layer** → TCP segments the data into packets
5. **Network Layer** → IP routes packets to the destination
6. **Data Link Layer** → MAC addresses determine the next hop
7. **Physical Layer** → Data is transmitted via Wi-Fi or Ethernet

---

## 🔹 TCP/IP Model (4 Layers)
### ✅ Overview
| OSI Layer Equivalent | TCP/IP Layer | Protocols & Functions |
|----------------------|-------------|------------------------|
| 7, 6, 5            | **Application**  | HTTP, FTP, SMTP, DNS |
| 4                  | **Transport**    | TCP, UDP |
| 3                  | **Internet**     | IP, ICMP, ARP |
| 2, 1               | **Network Access** | Ethernet, Wi-Fi |

### 📌 Key TCP/IP Protocols
- **TCP (Transmission Control Protocol)** → Reliable, connection-oriented
- **UDP (User Datagram Protocol)** → Fast, connectionless
- **IP (Internet Protocol)** → Routing and addressing
- **ICMP (Internet Control Message Protocol)** → Error handling (ping, traceroute)

---

## 🔹 Differences: OSI vs TCP/IP
| Feature            | OSI Model (7 Layers) | TCP/IP Model (4 Layers) |
|-------------------|------------------|------------------|
| Developed By     | ISO (International Organization for Standardization) | DARPA (U.S. Department of Defense) |
| Structure        | More detailed (7 layers) | Simplified (4 layers) |
| Use Case        | Theoretical reference model | Practical implementation for internet |
| Reliability      | Defines more functions | Focuses on core networking |

---

## 🔹 Common Networking Commands
```sh
# Check network configuration (Linux/macOS)
ip a

# Check network configuration (Windows)
ipconfig

# Test connectivity (Ping an IP)
ping 8.8.8.8

# Trace network route to a host
traceroute example.com   # Linux/macOS
tracert example.com      # Windows

# Show active TCP connections
netstat -ant
```

---

## 🔹 Best Practices in Networking
- **Use TCP for reliable communication** (e.g., HTTP, FTP, SMTP).
- **Use UDP for low-latency services** (e.g., VoIP, gaming, DNS).
- **Optimize routing with subnetting** to reduce network congestion.
- **Secure communication** using TLS (Application Layer) and VPNs (Network Layer).
- **Monitor network performance** using ICMP tools (`ping`, `traceroute`).

---