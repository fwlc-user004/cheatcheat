# 🔐 Cryptography & Password Cracking Cheatsheet

## 🔹 Introduction
Cryptography protects data using **encryption and hashing**, while password cracking techniques help **test and improve security measures** by identifying weak credentials.

---

## 🔹 Hashing Algorithms
| Algorithm | Description |
|-----------|-------------|
| **MD5** | Fast but insecure, prone to collisions |
| **SHA-1** | More secure than MD5 but still weak |
| **SHA-256** | Stronger cryptographic hashing |
| **bcrypt** | Adaptive hashing for password security |
| **PBKDF2 & Argon2** | Key derivation functions for strong password hashing |

### ✅ Hashing Example (Python)
```python
import hashlib
print(hashlib.sha256(b"password").hexdigest())
```

---

## 🔹 Symmetric Encryption
| Algorithm | Key Size | Usage |
|-----------|---------|-------|
| **AES** | 128/192/256-bit | File & data encryption |
| **DES** | 56-bit | Outdated, weak encryption |
| **3DES** | 168-bit | Better than DES but slow |
| **ChaCha20** | 256-bit | Fast and secure alternative |

### ✅ AES Encryption (Python)
```python
from Crypto.Cipher import AES
cipher = AES.new(b'sixteen byte key', AES.MODE_EAX)
ciphertext, tag = cipher.encrypt_and_digest(b"Secret Message")
```

---

## 🔹 Asymmetric Encryption
| Algorithm | Key Size | Usage |
|-----------|---------|-------|
| **RSA** | 2048-bit+ | Secure data exchange |
| **ECC** | 256-bit+ | Lightweight alternative to RSA |
| **Diffie-Hellman** | 1024-bit+ | Secure key exchange |
| **ElGamal** | 2048-bit+ | Secure cryptographic signatures |

### ✅ RSA Key Generation (OpenSSL)
```sh
openssl genpkey -algorithm RSA -out private_key.pem -pkeyopt rsa_keygen_bits:2048
openssl rsa -pubout -in private_key.pem -out public_key.pem
```

---

## 🔹 Password Cracking Techniques
| Method | Description |
|--------|-------------|
| **Brute-Force Attack** | Tries every possible password combination |
| **Dictionary Attack** | Uses a predefined list of passwords |
| **Rainbow Table Attack** | Precomputed hashes to find passwords |
| **Credential Stuffing** | Uses leaked credentials from breaches |

### ✅ Hashcat Example (Cracking MD5 Hash)
```sh
hashcat -m 0 -a 0 hash.txt rockyou.txt
```

### ✅ John the Ripper Example
```sh
john --wordlist=rockyou.txt --format=raw-md5 hash.txt
```

---

## 🔹 Steganography & Hidden Data Extraction
### ✅ Hide Data in an Image (Steghide)
```sh
steghide embed -cf image.jpg -ef secret.txt -p password
```

### ✅ Extract Hidden Data
```sh
steghide extract -sf image.jpg -p password
```

---

## 🔹 Best Practices
- **Use strong, unique passwords** and enforce MFA.
- **Store passwords securely** using bcrypt, PBKDF2, or Argon2.
- **Regularly audit password security** using cracking tools for testing.
- **Encrypt sensitive data** to protect against unauthorized access.

---