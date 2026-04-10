[[Fundimentals of cybersecurity]]
#virus  #hacking

#  Malicious Software 


## 📌 **Core Topics Covered**
1. **Malware Overview & Terminology**
2. **Viruses**
3. **Worms**
4. **Bots & Botnets**
5. **Rootkits**
6. **Countermeasures**

---

## 🦠 **Malware Overview**
- **Definition**: Malicious software inserted into a system to compromise confidentiality, integrity, or availability.
- **Categories**:
  - **Host-dependent**: Viruses, logic bombs, backdoors
  - **Independent**: Worms, bots
- **Key Terms**:
  - **Virus**: Attaches to programs, spreads via execution
  - **Worm**: Self-replicating, spreads over networks
  - **Trojan Horse**: Disguised as legitimate software
  - **Backdoor**: Unauthorized access
  - **Logic Bomb**: Triggers on condition
  - **Bot/Zombie**: Infected machine used in attacks
  - **Rootkit**: Hides presence, maintains access
  - **Payload**: Malicious action performed

---

## 🧬 **Viruses**
- **Phases**: Dormant → Propagation → Triggering → Execution
- **Structure**: Infection mechanism + Trigger + Payload
- **Classification**:
  - **By Target**: Boot sector, file infector, macro, multipartite
  - **By Concealment**: Encrypted, stealth, polymorphic, metamorphic
- **Examples**: Macro viruses, e-mail viruses (Melissa)
- **Countermeasures**:
  - **Prevention** (ideal but difficult)
  - **Detection** → Identification → Removal
  - **Anti-virus Generations**:
    1. Signature scanners
    2. Heuristics
    3. Behavior blocking
    4. Combination packages

---

## 📡 **Worms**
- **Definition**: Self-replicating program spreading over networks
- **Phases**: Same as viruses
- **Propagation**: Email, remote execution, scanning
- **Notable Worms**:
  - **Morris Worm** (1988): UNIX, password cracking, sendmail exploit
  - **Code Red**: IIS exploit, DDoS
  - **SQL Slammer**: Rapid spread via buffer overflow
  - **Mydoom**: Mass-mailing, backdoor installation
- **Propagation Model**: Exponential → Linear → Slow finish
- **Modern Worm Tech**: Multiplatform, multi-exploit, polymorphic, zero-day
- **Countermeasures**: Signature filtering, rate limiting, PWC (Proactive Worm Containment)

![[Screenshot_20260116_230853_Drive.jpg]]

---

## 🤖 **Bots & Botnets**
- **Bot**: Program taking over computers for coordinated attacks
- **Botnet**: Network of bots under centralized control
- **Uses**: DDoS, spamming, keylogging, malware spread
- **Characteristics**: Remote control (IRC/HTTP), spreading mechanism, attack software
- **Countermeasures**: IDS, honeypots, digital immune systems

---

## 🕵️ **Rootkits & Backdoors**
- **Rootkit**: Set of programs maintaining hidden admin access
- **Types**: Persistent vs. memory-based; user-mode vs. kernel-mode
- **Installation**: Via Trojan or hacker activity
- **Backdoor**: Secret entry point, often left by programmers
- **Countermeasures**: File integrity checks, host-based AV, network IDS

---

## 🛡️ **General Countermeasures**
- **Prevention**: Hardening, access controls, user education
- **Detection**: Monitoring, anomaly detection, signature analysis
- **Response**: Isolation, removal, recovery from backups
- **Layered Defense**: AV, firewalls, IDS, patch management

![[Screenshot_20260116_230730_Drive.jpg]]

---

## 📚 **Key Takeaways**
- Malware evolves rapidly; defense requires layered, adaptive strategies.
- Viruses require host programs; worms spread autonomously.
- Botnets enable large-scale, distributed attacks.
- Rootkits are stealthy and hard to detect; integrity checks are crucial.
- Modern threats: zero-day exploits, polymorphic/metamorphic code, multi-vector attacks.

---

## 🏷️ **Suggested Tags for Obsidian**

#malware #virus #worm #botnet #rootkit #cybersecurity #threats #countermeasures #antivirus #IDS #honeypot #propagation #DDoS
