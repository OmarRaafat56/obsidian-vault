[[Fundimentals of cybersecurity]]

---

## User Authentication

### 🔐 Overview
- **User authentication** is the process of verifying an identity claimed by or for a system entity.
- It consists of two steps:
  1. **Identification**: Presenting an identifier (e.g., username).
  2. **Verification**: Providing authentication info to bind the entity to the identifier.
- Distinct from **message authentication**.

---

### 📌 Four Means of Authentication
1. **Something you know** – Password, PIN, security questions.
2. **Something you have** – Token, smart card, key.
3. **Something you are (static biometrics)** – Fingerprint, face, retina.
4. **Something you do (dynamic biometrics)** – Voice, signature, typing rhythm.

---

### 🛡️ Assurance Levels
- Level 1: Little confidence (e.g., online forum)
- Level 2: Some confidence (e.g., professional orgs)
- Level 3: High confidence (e.g., patent applicants)
- Level 4: Very high confidence (e.g., sensitive systems)

---

### 🔓 Password Authentication
- Widely used but vulnerable.
- Attacks include:
  - Offline dictionary attacks
  - Specific account attacks
  - Password guessing
  - Workstation hijacking
  - Electronic monitoring

#### ✅ Countermeasures:
- Hash passwords with **salt** to prevent duplicates and slow attacks.
- Use strong hash functions (e.g., MD5, bcrypt).
- Enforce password policies (length, complexity).
- Limit login attempts, use account lockout.
- Educate users, use proactive/reactive checking.

![[Screenshot_20260116_224234_Drive.jpg]]

---

### 💳 Token-Based Authentication
- **Memory cards**: Store data (e.g., magnetic stripe).
- **Smart cards**: Contain a processor, memory, I/O ports.
  - Can use static passwords, dynamic passwords, or challenge-response.
- **USB dongles** are a common alternative.
- Used in eID cards (e.g., German national eID).

![[Screenshot_20260116_224639_Drive.jpg]]

---

### 👁️ Biometric Authentication
- Uses physical traits: face, fingerprint, iris, voice, etc.
- Process:
  - **Enrollment**: Capture biometric, create template.
  - **Verification/Identification**: Compare with stored template.
- **Accuracy issues**: False matches vs. false non-matches.
- **Iris recognition** is highly accurate and contactless.

![[Screenshot_20260116_225212_Drive.jpg]]

---

### 🌐 Remote User Authentication
- More complex due to eavesdropping and replay risks.
- Often uses **challenge-response protocols**:
  - Host sends random challenge (`r`).
  - User computes `f(r, hash(P))`.
  - Host verifies.

---

### 🛡️ Security Issues & Attacks
| Attack Type | Description | Countermeasure |
|-------------|-------------|----------------|
| **Client attack** | Guessing passwords | Strong passwords, attempt limits |
| **Host attack** | Targeting stored passwords | Hashing, protecting databases |
| **Eavesdropping** | Observing passwords | Multifactor auth, user diligence |
| **Replay attack** | Reusing captured data | Challenge-response, one-time codes |
| **Trojan horse** | Fake device/app to capture credentials | Trusted environment, client auth |
| **DoS attack** | Flooding auth service | Multifactor with token |

---

### 🏦 Case Study: ATM Security
- Older ATMs used dedicated lines to processors.
- Newer setups connect via bank networks, exposing transactions to internal/Internet attacks.
- Vulnerabilities: **confidentiality** and **integrity** of transaction data.

---

### ✅ Summary
- Authentication methods: passwords, tokens, biometrics.
- Each has strengths and weaknesses.
- Remote auth requires secure protocols.
- Real-world applications (e.g., iris biometrics in banking) show practical use and risks.

---

### 📚 Tags
#authentication #passwords #biometrics #tokens #security #cybersecurity #lecture-notes`

---

