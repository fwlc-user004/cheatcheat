# 🔥 iptables Comprehensive Cheatsheet

## 🔹 Introduction
**iptables** is a command-line firewall utility for managing **Linux kernel firewall rules**. It filters traffic based on rules defined by the user.

---

## 🔹 Checking iptables Rules
```sh
# List all rules in the default table
sudo iptables -L -v -n

# List rules with line numbers
sudo iptables -L --line-numbers
```

---

## 🔹 Basic Rules
### ✅ Allow SSH (Port 22)
```sh
sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
```

### ✅ Allow HTTP/HTTPS Traffic
```sh
sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 443 -j ACCEPT
```

### ✅ Drop All Incoming Traffic (Default Deny Policy)
```sh
sudo iptables -P INPUT DROP
```

---

## 🔹 Allow Specific IPs
### ✅ Allow a Single IP
```sh
sudo iptables -A INPUT -s 192.168.1.100 -j ACCEPT
```

### ✅ Allow a Subnet
```sh
sudo iptables -A INPUT -s 192.168.1.0/24 -j ACCEPT
```

### ✅ Block a Specific IP
```sh
sudo iptables -A INPUT -s 10.0.0.5 -j DROP
```

---

## 🔹 Port Forwarding & NAT
### ✅ Forward Port 8080 to 80
```sh
sudo iptables -t nat -A PREROUTING -p tcp --dport 8080 -j REDIRECT --to-port 80
```

### ✅ Masquerade Traffic (NAT)
```sh
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```

---

## 🔹 Logging & Monitoring
### ✅ Log Dropped Packets
```sh
sudo iptables -A INPUT -j LOG --log-prefix "[DROP] " --log-level 4
```

### ✅ View Logs
```sh
dmesg | grep DROP
```

---

## 🔹 Deleting & Flushing Rules
### ✅ Delete a Specific Rule
```sh
sudo iptables -D INPUT -s 192.168.1.100 -j ACCEPT
```

### ✅ Flush All Rules
```sh
sudo iptables -F
```

---

## 🔹 Save & Restore iptables Rules
### ✅ Save Rules
```sh
sudo iptables-save > /etc/iptables/rules.v4
```

### ✅ Restore Rules
```sh
sudo iptables-restore < /etc/iptables/rules.v4
```

---

## 🔹 Best Practices
- **Use default DROP policy** and allow only necessary traffic.
- **Whitelist known IPs** instead of relying on blacklisting.
- **Regularly backup iptables rules**.
- **Monitor logs** to detect suspicious activity.

---