[[Fundimentals of cybersecurity]]
# Software Security

## 📌 **1. Software Security vs Software Quality**
- **Software Quality / Reliability**:
    - Focuses on **accidental failures**
    - Triggered by normal/random inputs
    - Goal: Reduce bug frequency
- **Software Security**:
    - Attacker **crafts inputs deliberately**
    - Targets rare/unexpected bugs
    - Bugs often missed by standard testing

---

## 🛡️ **2. Defensive (Secure) Programming**
- Assume **nothing**, validate **everything**
- Check **all error states** explicitly
- Validate:
    - Inputs
    - Environment
    - Execution assumptions
- Security must be a **design goal**, not added later

---

## 🔍 **3. Handling Program Input Safely**
- **Input includes**:
    - Keyboard, files, network data
    - Environment variables
    - Configuration files
- **Two major concerns**:
    1. **Input size** → Buffer overflow
    2. **Input interpretation** → Misuse of data
- **Treat all input as untrusted**

---

## 📏 **4. Input Size & Buffer Overflow**
- **Common mistake**: Assuming input fits a fixed buffer
- **Secure practices**:
    - Use **dynamic buffers**
    - Process input in **chunks**
    - Always **check input length**

---

## 🧠 **5. Input Interpretation**
- Input may be **binary** or **text** (ASCII, Unicode, UTF-8)
- **Meaning matters**: Integer, filename, URL, email, identifier
- Failure to validate meaning → **exploitable vulnerabilities**

---

## 💉 **6. Injection Attacks**
- **Command Injection**: Input alters system commands (common in Perl, PHP, shell)
- **SQL Injection**: Manipulates SQL queries → read/modify/delete DB data
- **Code Injection**: Input contains executable code (e.g., PHP remote file inclusion)
- **Prevention**:
    - Validate input against allowed patterns
    - Escape/reject metacharacters
    - **Never trust user input**

---

## 🌐 **7. Cross-Site Scripting (XSS)**
- Malicious input from one user shown to others
- Injected scripts run in victim’s browser
- Common in: Guestbooks, Blogs, Forums
- Requires validating **both input and output**

---

## ✅ **8. Input Validation Techniques**
- Prefer **whitelisting** over blacklisting
- Use **regular expressions**
- **Reject or sanitize** invalid input
- Handle **alternate encodings** carefully

---

## 🔠 **9. Canonicalization & Encoding**
- Same character may have **multiple encodings**
- Unicode/UTF-8 allows redundant representations
- **Always**:
    1. Convert input to a **standard form**
    2. Then validate

---

## 🔢 **10. Numeric Input Validation**
- Risks:
    - Signed vs unsigned confusion
    - Integer overflow
- Can **bypass buffer size checks** if mishandled

---

## 🧪 **11. Fuzzing**
- Automated testing with **random inputs**
- Finds crashes and hidden bugs
- **Benefits**:
    - Cheap
    - Effective
    - Improves security and reliability

---

## ✍️ **12. Writing Safe Program Code**
- Ensure:
    - Correct algorithm implementation
    - Correct machine-level execution
    - Correct data usage
- Avoid:
    - Debug/backdoor code in production
    - Weak randomness
- **Strongly typed languages are safer**

---

## 🧠 **13. Memory Management**
- Dynamic memory must be allocated/freed correctly
- Errors cause:
    - **Memory leaks**
    - **Denial of Service**
- Languages with **automatic memory management are safer**

---

## ⚡ **14. Race Conditions**
- Occur when multiple processes/threads access **shared data**
- Without synchronization → **Data corruption, Deadlock**
- Use proper **locking and synchronization mechanisms**

---

## 🖥️ **15. Interaction with Operating System**
- OS provides:
    - Environment variables
    - File access
    - Shared resources
- **Environment variables are untrusted input**
- Common attack vectors: **PATH, IFS, LD_LIBRARY_PATH**

---

## 🛡️ **16. Principle of Least Privilege**
- Programs should run with **minimum required privileges**
- Limits damage if compromised
- Prefer:
    - Group privileges over full user privileges
    - **Dropping privileges after startup**

---

## 📄 **17. Temporary Files**
- Must be:
    - Unique
    - Unpredictable
    - Securely created
- Avoid predictable names (e.g., PID-based)
- Use **atomic file creation** (e.g., `mkstemp`)

---

## 🔗 **18. Program Interaction**
- Data between programs = **output → input**
- Validate assumptions when **chaining programs**
- Protect data:
    - Local: pipes, secure temp files
    - Network: TLS/SSL, SSH, IPSec

---

## 📤 **19. Handling Program Output**
- Output may be: **Stored, Transmitted, Displayed**
- Must:
    - Match expected format
    - Use correct encoding
- Output vulnerabilities often target the **viewer**, not the program

---

## ✅ **20. Overall Summary**
Secure software requires:
- Defensive programming
- Safe input handling
- Correct algorithms and memory use
- Least privilege
- Secure OS interaction
- Careful output handling

---

## 🏷️ **Suggested Tags for Obsidian**

#software-security #secure-programming #input-validation #injection #XSS #buffer-overflow #fuzzing #least-privilege #race-condition #temporary-files #defensive-coding #canonicalization
