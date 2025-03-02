# ☁️ Cloud & IoT Security Cheatsheet

## 🔹 Introduction
Cloud security involves **protecting cloud environments** (AWS, Azure, GCP), while IoT security focuses on **securing smart devices, embedded systems, and industrial IoT**.

---

## **🔹 Cloud Security**
### ✅ Common Cloud Security Threats
- **Misconfigurations** (Exposed S3 Buckets, Public Databases)
- **Weak IAM Policies** (Overprivileged Users, Unrestricted API Access)
- **Lack of Encryption** (Data in Transit & Rest)
- **Insecure APIs & Endpoints**
- **Cloud Malware & Ransomware Attacks**

### ✅ AWS Security Testing
#### 📌 Enumerate Public S3 Buckets
```sh
aws s3 ls s3://target-bucket --region us-east-1
```

#### 📌 List IAM Users & Policies
```sh
aws iam list-users
aws iam list-policies --scope Local
```

#### 📌 Identify Open Ports in EC2 Instances
```sh
nmap -p- ec2-xx-xx-xx-xx.compute.amazonaws.com
```

### ✅ Azure Security Testing
#### 📌 Enumerate Azure Storage Accounts
```sh
az storage account list --query "[].{name:name, location:location}"
```

#### 📌 Scan for Publicly Accessible VMs
```sh
az vm list-ip-addresses --output table
```

### ✅ Google Cloud Security Testing
#### 📌 List All GCP Buckets
```sh
gcloud storage buckets list
```

#### 📌 Check IAM Roles for GCP Resources
```sh
gcloud projects get-iam-policy my-project-id
```

---

## **🔹 IoT Security**
### ✅ Common IoT Security Issues
- **Weak or Default Credentials** (Hardcoded passwords in firmware)
- **Insecure Protocols** (Lack of encryption in MQTT, CoAP)
- **Unpatched Firmware Vulnerabilities**
- **Lack of Network Segmentation** (IoT devices on the same network as critical systems)

### ✅ IoT Device Enumeration
#### 📌 Scan for Open IoT Devices (Shodan)
```sh
shodan search "default password port:23"
```

#### 📌 Identify Open IoT Ports
```sh
nmap -p 22,23,80,443,1883 target-device-ip
```

### ✅ Firmware Security Testing
#### 📌 Extract Firmware for Analysis
```sh
binwalk -e firmware.bin
```

#### 📌 Search for Hardcoded Credentials
```sh
grep -i "password" extracted_files/
```

### ✅ Sniffing IoT Network Traffic
#### 📌 Capture Traffic from IoT Devices
```sh
tcpdump -i wlan0 host <device-ip> -w iot_traffic.pcap
```

#### 📌 Analyze MQTT Traffic
```sh
mosquitto_sub -h iot-broker.com -t "#" -v
```

---

## **🔹 Best Practices**
- **Enable Multi-Factor Authentication (MFA)** for cloud access.
- **Regularly audit cloud IAM roles** to remove excessive permissions.
- **Use network segmentation** to isolate IoT devices from critical infrastructure.
- **Encrypt data in transit and at rest** (TLS, AES, VPNs for IoT communication).
- **Perform continuous monitoring** using cloud security tools (AWS GuardDuty, Azure Security Center, GCP Security Command Center).

---