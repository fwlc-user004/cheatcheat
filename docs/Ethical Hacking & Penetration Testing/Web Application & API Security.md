# 🌐 Web Application & API Security Cheatsheet

## 🔹 Introduction
Web application security focuses on **protecting websites and APIs** from attacks that exploit vulnerabilities in code, authentication, and session management.

---

## 🔹 OWASP Top 10 Web Attacks
| Attack Type | Description |
|------------|-------------|
| **SQL Injection (SQLi)** | Injecting malicious SQL queries to manipulate databases |
| **Cross-Site Scripting (XSS)** | Injecting malicious scripts into web pages viewed by users |
| **Cross-Site Request Forgery (CSRF)** | Tricking a user into performing unintended actions |
| **Insecure Authentication** | Weak password policies, missing MFA, broken session management |
| **Security Misconfiguration** | Default credentials, excessive permissions, exposed debug info |

---

## 🔹 SQL Injection (SQLi)
### ✅ Detect SQL Injection
```sh
' OR '1'='1 --  # Bypass authentication
" OR "a"="a" --  # Test for SQLi vulnerability
```

### ✅ Exploit with SQLMap
```sh
sqlmap -u "http://example.com/login.php?id=1" --dbs  # Enumerate databases
sqlmap -u "http://example.com/login.php?id=1" --tables -D users  # Extract table names
```

### ✅ Prevent SQL Injection
- Use **prepared statements**:
```python
cursor.execute("SELECT * FROM users WHERE username = ?", (user_input,))
```
- Apply **input validation & sanitization**.

---

## 🔹 Cross-Site Scripting (XSS)
### ✅ Test for XSS Vulnerability
```html
<script>alert('XSS')</script>
<img src=x onerror=alert('XSS')>
```

### ✅ Prevent XSS
- Use **Content Security Policy (CSP)**:
```html
<meta http-equiv="Content-Security-Policy" content="default-src 'self'">
```
- **Sanitize user input** (e.g., `htmlspecialchars()` in PHP).

---

## 🔹 Cross-Site Request Forgery (CSRF)
### ✅ Test for CSRF Vulnerability
```html
<form action="http://example.com/delete_account" method="POST">
  <input type="submit" value="Delete Account">
</form>
```

### ✅ Prevent CSRF
- **Use CSRF tokens** in forms and requests.
- **Validate HTTP Referer headers**.

---

## 🔹 API Security
### ✅ API Enumeration
```sh
nmap --script=http-enum -p80,443 example.com  # Detect API endpoints
```

### ✅ API Exploitation
- **JWT Manipulation** (Change algorithm to `none`):
```json
{
  "alg": "none",
  "typ": "JWT"
}
```
- **Rate Limit Bypass** (Using Burp Suite Intruder or scripting rapid API calls).

### ✅ API Security Best Practices
- **Enforce authentication & authorization** (OAuth 2.0, API keys).
- **Limit API request rates** (Rate limiting, IP whitelisting).
- **Validate all input data** to prevent injections.

---

## 🔹 Automated Security Testing Tools
| Tool | Purpose |
|------|---------|
| **Burp Suite** | Web security testing |
| **OWASP ZAP** | Automated vulnerability scanning |
| **Nikto** | Web server vulnerability scanner |
| **SQLMap** | Automated SQL injection testing |
| **Postman** | API security testing |

---

## 🔹 Best Practices
- **Use HTTPS** to encrypt traffic.
- **Harden authentication mechanisms** (MFA, strong password policies).
- **Regularly update dependencies** to patch security vulnerabilities.
- **Implement proper logging & monitoring** to detect anomalies.

---