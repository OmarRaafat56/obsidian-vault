[[CCNA]]
Here’s a structured breakdown and summary of **Module 16: Network Security Fundamentals** from the Cisco *Introduction to Networks v7.0* (ITN) course. I’ve distilled the content into a clear, easy-to-review guide:

---

## **Module Title:** Network Security Fundamentals

**Module Objective:** Configure switches and routers with device hardening features to enhance security.

### **Topics & Objectives**

1. **Security Threats and Vulnerabilities** – Explain why basic security measures are necessary on network devices.
2. **Network Attacks** – Identify security vulnerabilities.
3. **Network Attack Mitigation** – Identify general mitigation techniques.
4. **Device Security** – Configure network devices with hardening features to mitigate security threats.

---

## **16.1 Security Threats and Vulnerabilities**

### **Types of Threats**

* **Threat actors**: Intruders who exploit software/hardware vulnerabilities.
* **Types of threats after access**:

  1. Information Theft
  2. Data Loss & Manipulation
  3. Identity Theft
  4. Disruption of Service

### **Types of Vulnerabilities**

1. **Technological Vulnerabilities** – OS weaknesses, TCP/IP weaknesses, network equipment flaws.
2. **Configuration Vulnerabilities** – Unsecured accounts, weak passwords, misconfigured services or devices.
3. **Security Policy Vulnerabilities** – Lack of written policies, improper access controls, missing disaster recovery plans.

### **Physical Security**

* Protect against threats to physical resources:

  1. **Hardware** – Damage to devices or cables
  2. **Environmental** – Temperature/humidity extremes
  3. **Electrical** – Power spikes, brownouts, total power loss
  4. **Maintenance** – Poor handling, missing spare parts, bad labeling

---

## **16.2 Network Attacks**

### **Malware Types**

* **Viruses** – Self-replicate by infecting other programs.
* **Worms** – Standalone self-replicating programs.
* **Trojan Horses** – Malicious software disguised as legitimate.

### **Network Attack Categories**

1. **Reconnaissance** – Scanning and mapping networks (using `nslookup`, `whois`, ping).
2. **Access Attacks** – Exploit authentication or services to gain unauthorized access.

   * Password attacks (brute-force, Trojans, sniffers)
   * Trust exploitation
   * Port redirection
   * Man-in-the-middle attacks
3. **Denial of Service (DoS)** – Overload resources to prevent legitimate access.

   * DDoS: Distributed from multiple compromised devices (botnet).

---

## **16.3 Network Attack Mitigation**

### **Defense-in-Depth**

* Layered security approach combining multiple devices/services:

  * VPN, ASA Firewall, IPS, ESA/WSA, AAA server

### **Other Mitigation Techniques**

* **Backups** – Regularly backup device configs and data; store offsite; validate integrity.
* **Updates & Patching** – Keep OS and antivirus software up-to-date to prevent worm/malware attacks.
* **AAA (Authentication, Authorization, Accounting)** – Control who can access the network, what actions they can perform, and log activities.
* **Firewalls** – Control traffic between networks and protect services.

  * Types: Packet filtering, application filtering, URL filtering, stateful packet inspection (SPI)
* **Endpoint Security** – Laptops, desktops, mobile devices must be protected through policies, antivirus, host intrusion prevention, and network access control.

---

## **16.4 Device Security**

### **Cisco AutoSecure**

* Simplifies securing routers. Key steps include:

  1. Change default usernames/passwords
  2. Restrict resource access
  3. Disable unnecessary services
  4. Apply software updates and patches

### **Password Security**

* Strong password practices:

  * ≥8–10 characters, mixed case, numbers, symbols
  * Avoid dictionary words, names, birthdates
  * Use passphrases
  * Rotate passwords frequently
  * Encrypt stored passwords (service password-encryption)
  * Set minimum lengths, login attempt limits, and timeouts for inactive sessions

### **SSH Configuration**

Steps to secure remote access via SSH:

1. Configure unique hostname
2. Set IP domain name
3. Generate RSA key (≥1024 bits recommended)
4. Create local username database
5. Authenticate vty lines using local database
6. Enable SSH (disable Telnet if not used)

### **Disable Unused Services**

* Free system resources and prevent exploits
* Verify open ports (`show ip ports all` or `show control-plane host open-ports`)
* Disable unnecessary default services

---

## **16.5 Module Summary**

* Threats: Information theft, data loss, identity theft, disruption
* Vulnerabilities: Technological, configuration, security policy
* Physical threats: Hardware, environmental, electrical, maintenance
* Malware: Virus, worm, Trojan horse
* Network attacks: Reconnaissance, access, DoS/DDoS
* Mitigations: Defense-in-depth, backups, patches, AAA, firewalls, endpoint security
* Device security: AutoSecure, strong passwords, SSH, disable unused services

---

If you want, I can also create a **one-page cheat sheet** for this entire module with **all threats, mitigations, and device hardening steps** in a super-compact table for quick study. It’s perfect for exams or practical labs.

Do you want me to do that?
