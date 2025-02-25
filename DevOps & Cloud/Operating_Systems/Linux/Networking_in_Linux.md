# 🏆 Networking in Linux Cheat Sheet

---

## 📌 1. Checking Network Configuration

### 🔹 Display Network Interfaces and IP Addresses
```sh
ip a         # Show all network interfaces and IP addresses
ifconfig     # Display network configuration (older command)
hostname -I  # Get the IP address of the system
```

### 🔹 Check Routing Table
```sh
ip route show  # Show current routing table
netstat -rn    # Display routing table (alternative)
```

### 🔹 Show Active Connections
```sh
netstat -tulnp  # List open ports and listening services
ss -tulnp       # Alternative to netstat, faster and more detailed
```

---

## 📌 2. Network Connectivity Testing

### 🔹 Ping a Host
```sh
ping 8.8.8.8    # Send ICMP packets to test network connectivity
ping -c 5 google.com  # Ping 5 times and stop
```

### 🔹 Check Domain Name Resolution
```sh
nslookup example.com  # Query DNS for IP resolution
dig example.com       # Detailed DNS lookup
host example.com      # Get IP address of a domain
```

### 🔹 Trace Network Route
```sh
traceroute example.com  # Show path packets take to a destination
mtr example.com         # Real-time traceroute tool
```

---

## 📌 3. Managing Network Interfaces

### 🔹 Bring Network Interface Up or Down
```sh
ip link set eth0 up    # Enable network interface
ip link set eth0 down  # Disable network interface
```

### 🔹 Assign a Static IP Address
```sh
ip addr add 192.168.1.100/24 dev eth0  # Assign IP to eth0
ip route add default via 192.168.1.1   # Set default gateway
```

### 🔹 Restart Network Services
```sh
systemctl restart networking  # Restart networking service
systemctl restart NetworkManager  # Restart NetworkManager service
```

---

## 📌 4. Managing Firewall Rules (iptables & UFW)

### 🔹 Using iptables
```sh
iptables -L          # List all firewall rules
iptables -A INPUT -p tcp --dport 22 -j ACCEPT  # Allow SSH traffic
iptables -A INPUT -j DROP  # Block all other incoming traffic
iptables-save > /etc/iptables.rules  # Save rules
```

### 🔹 Using UFW (Uncomplicated Firewall)
```sh
ufw enable           # Enable UFW firewall
ufw allow 22/tcp     # Allow SSH connections
ufw deny 80/tcp      # Deny HTTP traffic
ufw status           # Show firewall rules
```

---

## 📌 5. Network Packet Analysis

### 🔹 Capture Network Packets
```sh
tcpdump -i eth0  # Capture packets on eth0 interface
tcpdump -c 10 -i eth0  # Capture first 10 packets
tcpdump -n port 80  # Capture HTTP traffic
```

### 🔹 Analyze Network Traffic with Wireshark
```sh
wireshark &  # Launch Wireshark GUI
```

---

## 📌 6. File Transfer Over Network

### 🔹 Secure Copy (SCP)
```sh
scp file.txt user@remote:/home/user/  # Copy file to remote system
scp -r folder user@remote:/home/user/  # Copy folder to remote system
```

### 🔹 Rsync (Efficient File Synchronization)
```sh
rsync -avz source/ user@remote:/destination/  # Sync files securely
```

### 🔹 Download Files from a URL
```sh
wget http://example.com/file.zip  # Download file
curl -O http://example.com/file.zip  # Alternative to wget
```

---

## 📌 7. SSH (Secure Shell) and Remote Access

### 🔹 Connect to a Remote Server
```sh
ssh user@remote_ip  # SSH into a remote system
ssh -p 2222 user@remote_ip  # Connect using a custom port
```

### 🔹 Generate SSH Key and Copy to Remote Server
```sh
ssh-keygen -t rsa   # Generate SSH key pair
ssh-copy-id user@remote_ip  # Copy key to remote server
```

---

## 📌 8. Network Services Management

### 🔹 Checking Open Ports
```sh
netstat -tulnp  # List open ports and services
ss -tulnp       # Alternative to netstat
```

### 🔹 Start/Stop Network Services
```sh
systemctl start apache2  # Start Apache web server
systemctl stop apache2   # Stop Apache web server
systemctl restart apache2  # Restart Apache
```

---
