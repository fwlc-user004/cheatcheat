# 🕵️ Wireshark Comprehensive Cheatsheet

## 🔹 Introduction
Wireshark is a **network protocol analyzer** that captures and inspects packets in real-time to analyze network traffic and detect security threats.

---

## 🔹 Installing Wireshark
```sh
# Install on Ubuntu/Debian
sudo apt update && sudo apt install wireshark -y

# Install on macOS
brew install --cask wireshark
```

---

## 🔹 Starting a Capture
### ✅ Open Wireshark & Select an Interface
1. Open **Wireshark**.
2. Select the **network interface** (e.g., Wi-Fi or Ethernet).
3. Click **Start Capture**.

### 📌 Start Wireshark from Command Line
```sh
wireshark -i eth0 -k
```

---

## 🔹 Filtering Packets
### ✅ Common Display Filters
| Filter                  | Description |
|-------------------------|-------------|
| `ip.src == 192.168.1.1` | Show packets from a specific source IP |
| `ip.dst == 10.0.0.1`    | Show packets to a specific destination IP |
| `tcp.port == 80`        | Show only HTTP traffic |
| `udp.port == 53`        | Show only DNS traffic |
| `http`                  | Show only HTTP packets |
| `tcp.flags.syn == 1`    | Show only SYN packets (used in TCP handshake) |
| `tcp.analysis.flags`    | Show TCP retransmissions and errors |

---

## 🔹 Capture Filters (Before Starting Capture)
```sh
# Capture only TCP packets
tcp

# Capture only UDP packets
udp

# Capture only HTTP traffic
port 80

# Capture traffic from a specific IP
host 192.168.1.1
```

---

## 🔹 Analyzing Packets
### ✅ TCP Handshake
1. **SYN** → Client initiates connection.
2. **SYN-ACK** → Server acknowledges.
3. **ACK** → Connection established.

Filter to see handshake:
```sh
tcp.flags.syn == 1 || tcp.flags.ack == 1
```

### 📌 Follow a TCP Stream
1. Right-click on a TCP packet.
2. Select **Follow > TCP Stream**.

---

## 🔹 Exporting & Saving Captures
### ✅ Save a Capture File
```sh
# Save capture in pcap format
wireshark -w capture.pcap -i eth0
```

### 📌 Open a pcap File
```sh
wireshark -r capture.pcap
```

---

## 🔹 Wireshark Best Practices
- **Use capture filters** to reduce unnecessary data.
- **Save captures in .pcap format** for future analysis.
- **Apply display filters** to focus on relevant traffic.
- **Analyze TCP handshake** for connection issues.
- **Check for anomalies** (e.g., excessive SYN packets indicating scanning attempts).

---