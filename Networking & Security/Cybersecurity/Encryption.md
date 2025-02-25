# 🔐 Encryption (AES, RSA, Hashing Algorithms) Comprehensive Cheatsheet

## 🔹 Introduction
Encryption secures data by **converting plaintext into ciphertext** using cryptographic algorithms. The three primary categories include **Symmetric Encryption (AES), Asymmetric Encryption (RSA), and Hashing Algorithms**.

---

## 🔹 AES (Advanced Encryption Standard)
### ✅ Overview
- **Symmetric encryption** (same key for encryption & decryption).
- **Block cipher** with key sizes **128-bit, 192-bit, or 256-bit**.
- Used in **SSL/TLS, VPNs, and file encryption**.

### 📌 AES Encryption (Python Example)
```python
from Crypto.Cipher import AES
from Crypto.Random import get_random_bytes

key = get_random_bytes(16)  # 128-bit key
aes = AES.new(key, AES.MODE_EAX)
ciphertext, tag = aes.encrypt_and_digest(b'Hello, World!')
```

### 📌 AES Decryption
```python
aes = AES.new(key, AES.MODE_EAX, nonce=aes.nonce)
decrypted = aes.decrypt(ciphertext)
print(decrypted.decode())
```

---

## 🔹 RSA (Rivest-Shamir-Adleman)
### ✅ Overview
- **Asymmetric encryption** (public/private key pair).
- Used in **SSL/TLS, digital signatures, and secure messaging**.
- Key sizes: **2048-bit and 4096-bit** recommended.

### 📌 Generate RSA Keys (Linux)
```sh
openssl genpkey -algorithm RSA -out private_key.pem -pkeyopt rsa_keygen_bits:2048
openssl rsa -pubout -in private_key.pem -out public_key.pem
```

### 📌 Encrypt Data (Python)
```python
from Crypto.PublicKey import RSA
from Crypto.Cipher import PKCS1_OAEP

key = RSA.import_key(open("public_key.pem").read())
cipher = PKCS1_OAEP.new(key)
ciphertext = cipher.encrypt(b"Secure Message")
```

### 📌 Decrypt Data
```python
key = RSA.import_key(open("private_key.pem").read())
cipher = PKCS1_OAEP.new(key)
decrypted = cipher.decrypt(ciphertext)
print(decrypted.decode())
```

---

## 🔹 Hashing Algorithms
### ✅ Overview
- **One-way functions** (cannot be reversed).
- Used in **password storage, data integrity, and digital signatures**.
- Common algorithms: **MD5, SHA-1, SHA-256, bcrypt**.

### 📌 Hashing in Python
```python
import hashlib

hash_sha256 = hashlib.sha256(b'password123').hexdigest()
print(hash_sha256)
```

### 📌 Secure Password Hashing (bcrypt)
```python
import bcrypt

password = b"supersecret"
hashed = bcrypt.hashpw(password, bcrypt.gensalt())
print(hashed)
```

---

## 🔹 Best Practices
- **Use AES-256 for strong symmetric encryption.**
- **Use RSA-2048 or higher** for secure asymmetric encryption.
- **Use SHA-256 or bcrypt for password hashing** (avoid MD5 & SHA-1).
- **Never store encryption keys with encrypted data.**
- **Implement salting for password security.**

---