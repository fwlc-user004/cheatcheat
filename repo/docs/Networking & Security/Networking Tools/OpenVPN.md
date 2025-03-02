# 🔐 OpenVPN Comprehensive Cheatsheet

## 🔹 Introduction
OpenVPN is an open-source **VPN solution** that allows secure **point-to-point** or **site-to-site** connections using **TLS/SSL encryption**.

---

## 🔹 Installing OpenVPN
```sh
# Install OpenVPN on Ubuntu/Debian
sudo apt update && sudo apt install openvpn -y

# Install OpenVPN on CentOS/RHEL
sudo yum install -y epel-release
sudo yum install -y openvpn
```

---

## 🔹 Setting Up OpenVPN Server
### ✅ Generate Server Keys & Certificates
```sh
# Initialize PKI
./easyrsa init-pki

# Build CA (Certificate Authority)
./easyrsa build-ca

# Generate Server Certificate & Key
./easyrsa build-server-full server nopass

# Generate Diffie-Hellman Parameters
./easyrsa gen-dh
```

### 📌 Configure OpenVPN Server
Edit the OpenVPN server config file (`/etc/openvpn/server.conf`):
```ini
port 1194
proto udp
dev tun
ca ca.crt
cert server.crt
key server.key
dh dh.pem
server 10.8.0.0 255.255.255.0
push "redirect-gateway def1"
push "dhcp-option DNS 8.8.8.8"
keepalive 10 120
cipher AES-256-CBC
comp-lzo
persist-key
persist-tun
status openvpn-status.log
verb 3
```

### ✅ Start OpenVPN Server
```sh
sudo systemctl start openvpn@server
sudo systemctl enable openvpn@server
```

---

## 🔹 Setting Up OpenVPN Client
### ✅ Generate Client Certificate & Key
```sh
./easyrsa build-client-full client1 nopass
```

### 📌 Client Configuration (`client.ovpn`)
```ini
client
dev tun
proto udp
remote your-vpn-server-ip 1194
resolv-retry infinite
nobind
persist-key
persist-tun
remote-cert-tls server
cipher AES-256-CBC
comp-lzo
verb 3
ca ca.crt
cert client1.crt
key client1.key
```

### ✅ Start OpenVPN Client
```sh
sudo openvpn --config client.ovpn
```

---

## 🔹 Firewall & Routing Configuration
### ✅ Enable IP Forwarding
```sh
sudo sysctl -w net.ipv4.ip_forward=1
```

### ✅ Configure NAT with iptables
```sh
sudo iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -o eth0 -j MASQUERADE
```

---

## 🔹 Debugging & Logs
### ✅ Check OpenVPN Logs
```sh
sudo journalctl -u openvpn@server --no-pager
```

### ✅ Test Connection
```sh
ping -c 4 10.8.0.1
```

---

## 🔹 Best Practices
- **Use strong encryption** (AES-256, TLS 1.2+).
- **Restrict VPN access** using firewall rules.
- **Rotate client certificates regularly**.
- **Enable logging** for monitoring & troubleshooting.
- **Use MFA for additional security**.

---
