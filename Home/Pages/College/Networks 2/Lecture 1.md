[[Networks 2]]

# Network Function Virtualization (NFV)

**Course:** SIT324 – Computer Networks II

---

# Network Function Virtualization (NFV)

## 📌 Agenda Overview

* Definitions
* Motivation
* Challenges
* Flexibility
* From Hardware → Software
* Requirements
* Firewall Case Study
* NFV Platforms

---

# 1️⃣ Virtualization Basics

## 🔹 What is Virtualization?

Transparent abstraction of computing resources.

* Multiple logical views of physical hardware
* Decouples software from hardware

### Examples

* Virtual Machines (VMware, Xen)
* Storage Virtualization (SAN)
* Data Center Virtualization

---

# 2️⃣ Network Virtualization vs NFV

## 🔹 Network Virtualization

* Creates **multiple logical networks** from one physical network.

## 🔹 Network Function Virtualization (NFV)

* Virtualizes **network services**
* Runs services (firewall, NAT, IPS, load balancer) on **VMs instead of hardware appliances**

> Network Virtualization = virtual networks
> NFV = virtual network functions

---

# 3️⃣ What is NFV?

## 🔹 Definition

NFV decouples network functions from proprietary hardware so they can run as software on standard servers.

### Examples of Virtualized Functions

* NAT
* Firewall
* Intrusion Detection System (IDS)
* DNS
* Caching
* Load Balancer

---

## 🔹 Key Characteristics

* Hardware replaced by software
* Functions can run anywhere in infrastructure
* Services can be created, modified, scaled, and destroyed dynamically
* Orchestration across physical and virtual components

---

## ⚠️ What Cannot Be Virtualized?

Physical signal-based devices:

* Antennas
* Sensors
* Wireless receivers

---

# 4️⃣ Motivation for NFV

## 🔹 Modern Data Center Challenges

* Massive scale (100,000+ servers)
* Many hardware appliances
* Limited rack space and power
* High capital expenditure (CAPEX)
* Complex integration
* Rapid hardware obsolescence

---

## 🔹 Operational Problems

* Idle hardware
* Rare specialized skills required
* Difficult upgrades
* Repeated deployment cycles with little new revenue

---

## 🔹 Why We Need NFV

* Virtualization (location-independent resources)
* Orchestration (manage thousands of devices)
* Programmability (dynamic behavior changes)
* Dynamic Scaling
* Automation
* Visibility & Monitoring
* Performance Optimization
* Service Integration

---

# 5️⃣ NFV Flexibility

## 🔹 Cost & Resource Efficiency

* Uses commodity off-the-shelf servers
* Better resource utilization
* Reduces unused hardware

### Example

A server used today as:

* Firewall
  Tomorrow can be:
* VPN Gateway

Only software changes required.

---

## 🔹 Operational Benefits

* No physical cable reconfiguration
* Reduced downtime
* Easier scaling
* Faster innovation via software

---

# 6️⃣ From Hardware to Software

## 🔹 Transition Requirements

* Separate software from hardware
* Replace physical interfaces with virtual ones
* Standardize server platforms
* Convert hardware functions into VNFs (Virtual Network Functions)

---

# 7️⃣ NFV Challenges

## 🔹 1. Standardization

Risk of incompatible proprietary orchestration solutions.

---

## 🔹 2. Vendor Lock-in (Walled Garden NFV)

* Closed ecosystems
* Limited interoperability
* Monopoly risk

Solution → Open standards & open source

---

## 🔹 3. New Operations Model

NFV cannot be managed like traditional hardware.
Requires:

* End-to-end service management
* Automation-first architecture

---

# 8️⃣ NFV Requirements

## 🔹 1. Interoperability

* Run VNFs from different vendors
* Unified interfaces
* Hardware/software decoupling

---

## 🔹 2. Performance Trade-Off

Software may be slower than hardware.

Mitigation:

* Efficient hypervisors
* Modern software optimization
* Minimize latency & throughput degradation

---

## 🔹 3. Migration Support

Hybrid networks:

* Physical appliances
* Virtual appliances

Smooth transition required.

---

## 🔹 4. Management & Orchestration

* Centralized orchestration
* Automation is mandatory
* Scalable architecture

---

## 🔹 5. Security & Resilience

* No degradation in security
* Maintain availability
* Handle failures & cyber attacks

---

## 🔹 6. Network Stability

* Must remain stable during:

  * Relocation
  * Reconfiguration
  * Failures

---

## 🔹 7. Integration

* Mix & match:

  * Servers
  * Hypervisors
  * VNFs
* Low integration cost
* Avoid vendor lock-in

---

# 9️⃣ NFV Case Study: Firewall Appliances

## 🔹 Traditional Firewall

Single appliance provides:

* Stateful filtering
* Deep Packet Inspection (DPI)
* NAT
* PAT

### Problems:

* Catch-all device
* Complex configuration
* Hard to scale
* Risk of single point of failure

---

## 🔹 Firewall Services Explained

### 1️⃣ Stateful Filtering

Tracks sessions and blocks unsolicited responses.

---

### 2️⃣ Deep Packet Inspection (DPI)

Inspects packet content for:

* Applications
* Malware
* Attack patterns

---

### 3️⃣ NAT (Network Address Translation)

One-to-one IP mapping.

Example:

```
10.1.2.20 → 33.3.2.20
```

---

### 4️⃣ PAT (Port Address Translation)

Many-to-one IP mapping using ports.

Example:

```
192.168.3.10 → 24.30.10.10:5000
```

---

# 🔟 NFV Firewall Solutions

## 🔹 First Solution: Multiple Virtual Firewalls

* One firewall per service
* Separate virtual topologies

### Advantages:

* Service-specific configuration
* Independent scaling
* Independent upgrades

### Disadvantages:

* Each firewall must support full features
* Configuration synchronization required
* Operational complexity

---

## 🔹 Second Solution: Disaggregated Firewall (Best Practice)

Break firewall into separate VNFs:

* DPI service
* NAT service
* Stateful inspection service

### Advantages:

* Service specialization
* Independent scaling
* Optimized placement
* Better performance
* Reduced complexity

---

# 1️⃣1️⃣ NFV Platforms

## 🔹 Popular NFV Platforms

* OpenStack
* VMware vCloud NFV
* Cisco NFV

---

## 🔹 Common Virtual Network Functions

### Virtual Router

* Packet forwarding
* Routing protocols
* NAT
* Policy-based routing

---

### Virtual Firewall

* L3–L7 filtering
* Stateful/stateless
* DPI
* IDS/IPS

---

### Virtual Load Balancer

* L4–L7 load balancing
* Virtual IP (VIP)
* NAT support

---

# 📌 Key Takeaways

* NFV replaces hardware appliances with software VNFs.
* Enables flexibility, scalability, and automation.
* Reduces cost and hardware dependency.
* Requires strong orchestration and open standards.
* Disaggregation improves scalability and specialization.
* Hybrid physical + virtual networks are necessary during migration.

---

# 🏷️ Tags


#ComputerNetworks
#SIT324
#NFV
#NetworkFunctionVirtualization
#Virtualization
#CloudNetworking
#DataCenter
#Firewall
#NAT
#PAT
#DPI
#Orchestration
#OpenStack
#VMware
#Cisco
#VirtualNetworkFunctions


---

