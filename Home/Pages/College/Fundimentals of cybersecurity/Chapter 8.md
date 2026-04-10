[[Fundimentals of cybersecurity]]

# Software Security (Part 2)

## 📌 **Core Principles**
- **Security is an ongoing process**, not a one-time activity.
- Ensures: **Confidentiality, Integrity, Availability (CIA)**.
- Secure software is built by **security-aware developers** from the **design phase**.
- Adding security later is **costly and ineffective**.

---

## 🔐 **Secure Development & QA**
- **Quality Assurance (QA)** must include **security testing**.
- Detect security defects **before release** to reduce:
  - Post-release vulnerabilities
  - Cost of fixes
  - Risk to users/systems

---

## 📖 **Secure Code Review**
- **Final security checkpoint** before release.
- **Focus Areas**:
  - Authentication & Authorization
  - Security Configuration
  - Session Management
  - Input Validation & Error Handling
  - Logging & Encryption
- **Reviewers must**:
  - Know the programming language
  - Understand secure coding practices

### ✍️ **Writing Secure Code Review Findings**
A good finding includes:
1. **Clear, descriptive title**
2. **Location** of vulnerability in code
3. **Detailed description**
4. **Risk impact** (what an attacker can do)
5. **Remediation recommendations**
6. **References** (OWASP, CWE, etc.)

---

## 🛠️ **Software Vulnerabilities**
- Weaknesses that allow attackers to compromise **CIA**.
- Attackers aim to:
  - Gain unauthorized privileges
  - Steal or manipulate data
- **Awareness is essential for prevention**.

---

## 🚨 **Top 10 Common Software Vulnerabilities (CWE)**
1. **SQL Injection**
2. **Cross-Site Scripting (XSS)**
3. **OS Command Injection**
4. **Classic Buffer Overflow**
5. **Integer Overflow**
6. **Unrestricted File Upload**
7. **Reliance on Untrusted Inputs in Security Decisions**
8. **Use of Hard-Coded Credentials**
9. **Missing Authentication for Critical Functions**
10. **Missing Encryption of Sensitive Data**

---

## 📍 **Detailed Vulnerability Breakdown**

### 1. **SQL Injection**
- **Cause**: Dynamic SQL without input sanitization.
- **Impact**: Bypass auth, read/modify DB data.
- **Prevention**: Parameterized queries, input validation, least-privilege DB accounts.

### 2. **Cross-Site Scripting (XSS)**
- **Impact**: Cookie theft, session hijacking, credential theft.
- **Prevention**: Output encoding, input validation, Content Security Policy (CSP).

### 3. **OS Command Injection**
- **Impact**: Arbitrary command execution (e.g., delete files).
- **Prevention**: Avoid system calls with user input, input validation, safe APIs.

### 4. **Classic Buffer Overflow**
- **Common in**: C/C++.
- **Impact**: Crashes, arbitrary code execution.
- **Prevention**: Bounds checking, safer functions, memory-safe languages.

### 5. **Integer Overflow**
- **Dangerous in**: Memory allocation, loop control.
- **Prevention**: Range checks, safer arithmetic libraries.

### 6. **Unrestricted File Upload**
- **Impact**: Remote code execution via malicious files.
- **Prevention**: File type validation, rename files, store outside web root.

### 7. **Reliance on Untrusted Inputs**
- **Examples**: Cookies, hidden fields, env variables.
- **Prevention**: Server-side validation, cryptographic integrity checks.

### 8. **Hard-Coded Credentials**
- **Risk**: Full system compromise.
- **Prevention**: External secure storage, environment variables, secrets management.

### 9. **Missing Authentication for Critical Functions**
- **Prevention**: Enforce auth checks, Role-Based Access Control (RBAC).

### 10. **Missing Encryption of Sensitive Data**
- **Risk**: Exposure of credentials, personal data.
- **Prevention**: Strong encryption, secure key management, TLS for transit.

---

## ✅ **Key Takeaways**
- Secure software requires:
  - Secure development practices
  - Security-aware QA
  - Thorough code reviews
- **Most vulnerabilities are preventable**.
- **Early detection saves cost and reduces risk**.

---

## 🏷️ **Suggested Tags for Obsidian**

#software-security #secure-coding #vulnerabilities #CWE #SQL-injection #XSS #buffer-overflow #encryption #authentication #code-review #OWASP #QA #cybersecurity
