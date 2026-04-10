[[Fundimentals of cybersecurity]]
#Networks
---

## Firewalls and Intrusion Prevention Systems

### 🔥 Overview
- Firewalls are a **perimeter defense** that creates a **single choke point** between a trusted internal network and an untrusted external network (like the Internet).
- Essential for protecting LANs while allowing controlled external access.

---

### 🛡️ Firewall Access Policy
- A firewall’s effectiveness depends on a well-defined **access policy**.
- Policy should specify:
  - Authorized traffic types
  - Source/destination addresses
  - Protocols, applications, content types
- Developed from organizational **risk assessment** and security policy.

---

### ✅ Firewall Capabilities
1. **Single choke point** for security enforcement.
2. **Monitoring point** for security events.
3. Platform for **non-security functions** (NAT, logging).
4. Can implement **IPSec for VPNs**.

### ❌ Firewall Limitations
- Cannot protect against:
  - Attacks that bypass it (dial-up, modems).
  - Internal threats.
  - Unsecured wireless LANs.
  - Infected portable devices.

---

### 🔍 Types of Firewalls

#### 1. **Packet Filtering Firewall**
- Filters based on **IP/TCP headers** (addresses, ports, protocols).
- Rules applied per packet; default policies:
  - **Default discard**: “What is not expressly permitted is prohibited.”
  - **Default forward**: “What is not expressly prohibited is permitted.”
- **Weaknesses**: Cannot inspect payload, limited logging, vulnerable to IP spoofing, tiny fragment attacks, misconfiguration.

#### 2. **Stateful Inspection Firewall**
- Tracks **TCP connections** and their states.
- Maintains a **connection table** to allow return traffic only for established sessions.
- More secure than simple packet filtering; can prevent session hijacking.

#### 3. **Application-Level Gateway (Proxy)**
- Acts as a **relay** for application traffic (e.g., HTTP, FTP).
- Requires **proxy code** for each application.
- Can restrict application features and log all traffic.
- **Higher overhead** but more secure.

#### 4. **Circuit-Level Gateway**
- Sets up **two TCP connections** (internal ↔ gateway ↔ external).
- Relays traffic **without inspecting content**.
- Often used for outbound traffic from trusted users.

![[Screenshot_20260116_225439_Drive.jpg]]


![[Screenshot_20260116_225926_Drive.jpg]]

---

### 🏠 Firewall Basing & Hosting

#### **Bastion Host**
- Critical strongpoint in network security.
- Runs a **secure OS**, minimal services, proxy applications.
- Each proxy is **small, independent, and auditable**.

#### **Host-Based Firewall**
- Software on individual servers/workstations.
- **Tailored rules** per host.
- Provides additional layer inside the network.

#### **Personal Firewall**
- For PCs/workstations (home or corporate).
- Can be software or built into home routers.
- Blocks unauthorized access and monitors outgoing traffic.

---

### 📍 Firewall Locations & Topologies

#### **Common Layouts:**
- **External firewall** at network edge.
- **Internal firewall(s)** inside the network.
- **DMZ (Demilitarized Zone)** between firewalls for public-facing servers.

![[Screenshot_20260116_230149_Drive.jpg]]
#### **Topologies:**
- **Screening router**: Single router with filtering (SOHO).
- **Single bastion inline**: Firewall between internal/external routers.
- **Single bastion T**: Adds DMZ via third NIC.
- **Double bastion inline**: DMZ sandwiched between two firewalls.
- **Distributed firewall**: Combination of standalone + host-based firewalls under central management.

![[Screenshot_20260116_230422_Drive.jpg]]

---

### 🌐 VPNs & IPSec
- **IPSec** can be implemented in firewalls to support **VPNs**.
- Encrypts traffic between sites over public networks.
- Placement options:
  - In firewall (common)
  - Separate box behind firewall
  - In boundary router (less secure)

![[Screenshot_20260116_230300_Drive.jpg]]

---

### 🛡️ Intrusion Prevention Systems (IPS)

#### **What is an IPS?**
- An **inline IDS** that can **block/discard malicious traffic**.
- Combines **firewall blocking** with **IDS detection algorithms**.
- Can be **network-based (NIPS)** or **host-based (HIPS)**.

#### **Host-Based IPS (HIPS)**
- Uses **signature + anomaly detection**.
- Monitors system calls, file access, registry, I/O.
- Can **sandbox suspicious code** (e.g., Java applets).

#### **Network-Based IPS (NIPS)**
- Inline device that can **drop packets or tear down TCP connections**.
- Techniques:
  - **Pattern matching**
  - **Stateful matching**
  - **Protocol anomaly detection**
  - **Traffic anomaly detection**

---

### 📦 Unified Threat Management (UTM)
- **All-in-one security appliance** combining:
  - Firewall
  - IPS
  - Antivirus
  - Web filtering
  - Anti-spam
  - VPN
  - Bandwidth shaping
- Traffic is **decrypted → inspected → re-encrypted** as needed.

![[Screenshot_20260116_230545_Drive.jpg]]

---

### ✅ Summary
- Firewalls provide **perimeter security** via packet filtering, stateful inspection, proxies, and circuit gateways.
- Can be deployed as **bastion hosts, host-based, personal, or distributed**.
- **IPS** adds **active blocking** to intrusion detection.
- **UTM** integrates multiple security functions into one device.

---

### 📚 Tags
#firewall #IPS #cybersecurity #network-security #DMZ #VPN #UTM #lecture-notes`

---

