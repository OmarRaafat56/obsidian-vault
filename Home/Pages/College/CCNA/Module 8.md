[[CCNA]]


---

# Module 8 – Network Layer

**Course:** Introduction to Networks (ITN v7.0)
**Module Objective:** Explain how the **network layer** uses IP protocols to enable communication across networks.

---

## 🌐 8.1 Network Layer Characteristics

### Purpose of the Network Layer (Layer 3)

The **Network Layer** enables **end-to-end communication across multiple networks**.

Primary functions:

* **Addressing** end devices
* **Encapsulation** of transport layer segments
* **Routing** packets across networks
* **De-encapsulation** at the destination

📌 Main protocols:

* **IPv4**
* **IPv6**

---

## 📦 IP Encapsulation

* IP encapsulates **Layer 4 segments** (TCP/UDP)
* Can use **IPv4 or IPv6** without affecting Layer 4
* IP packets are examined by **every Layer 3 device**
* **Source and destination IP addresses do NOT change** end-to-end

  * ⚠️ Exception: **NAT** (covered later)

---

## 🧠 Characteristics of IP

IP is designed for **low overhead** and is described as:

### 1️⃣ Connectionless

* No session setup before sending packets
* No synchronization or acknowledgments
* Packets are sent independently
* Connection-oriented reliability is handled by **TCP**

---

### 2️⃣ Best Effort

* No guarantee of delivery
* No retransmissions
* No acknowledgments
* No awareness of destination availability

📌 If reliability is needed → **Transport Layer (TCP)** handles it

---

### 3️⃣ Media Independent

* IP does **not** care about:

  * Frame type (Layer 2)
  * Media type (Layer 1)
* Works over:

  * Copper
  * Fiber
  * Wireless

---

## 📏 MTU and Fragmentation

* MTU (Maximum Transmission Unit) is learned from **Data Link Layer**
* If packet is larger than MTU:

  * **IPv4:** packet may be fragmented
  * **IPv6:** routers do **not** fragment packets

⚠️ Fragmentation:

* Causes latency
* Occurs when moving to a network with a smaller MTU

---

## 8.2 IPv4 Packet

### IPv4 Overview

* Primary Layer 3 protocol (historically)
* Header provides:

  * Direction
  * Processing information
  * Control details
* Header is read **left to right**, 4 bytes per line

---

### Important IPv4 Header Fields

| Field                        | Purpose                                      |
| ---------------------------- | -------------------------------------------- |
| Version                      | Identifies IPv4 (0100)                       |
| Differentiated Services (DS) | QoS (DiffServ / ToS)                         |
| Header Checksum              | Detects header corruption                    |
| Time to Live (TTL)           | Hop count; packet discarded at 0             |
| Protocol                     | Identifies Layer 4 protocol (TCP, UDP, ICMP) |
| Source IPv4 Address          | 32-bit sender address                        |
| Destination IPv4 Address     | 32-bit receiver address                      |

📌 Every router examines these fields

---

## 8.3 IPv6 Packets

### Limitations of IPv4

* **Address depletion**
* **Loss of end-to-end connectivity** due to NAT
* **Increased complexity** and latency from NAT

---

## 🌍 IPv6 Overview

Developed by the **IETF** to replace IPv4.

Improvements:

* **128-bit address space**
* Simplified header
* Better packet handling
* Eliminates need for NAT
* Restores end-to-end connectivity

---

## 🧾 IPv6 Header Characteristics

* Fixed size: **40 bytes**
* Simplified (fewer fields)
* No header checksum
* No router-based fragmentation

Removed IPv4 fields:

* Flags
* Fragment Offset
* Header Checksum

---

### Important IPv6 Header Fields

| Field                    | Purpose                                     |
| ------------------------ | ------------------------------------------- |
| Version                  | Identifies IPv6 (0110)                      |
| Traffic Class            | QoS (similar to DS field)                   |
| Flow Label               | Identifies packet flows (20-bit)            |
| Payload Length           | Length of payload                           |
| Next Header              | Identifies next protocol (TCP, UDP, ICMPv6) |
| Hop Limit                | Replaces TTL                                |
| Source IPv6 Address      | 128-bit source                              |
| Destination IPv6 Address | 128-bit destination                         |

---

## 🧩 IPv6 Extension Headers

* Optional
* Placed between IPv6 header and payload
* Used for:

  * Fragmentation
  * Security
  * Mobility

📌 Routers **do not fragment IPv6 packets**

---

## 8.4 How a Host Routes

### Host Forwarding Decisions

Packets are always created at the **source host**.

A host can send packets to:

* **Itself**

  * IPv4: `127.0.0.1`
  * IPv6: `::1`
* **Local hosts** (same LAN)
* **Remote hosts** (different network)

---

### Determining Local vs Remote

* **IPv4:** IP address + subnet mask
* **IPv6:** Network prefix advertised by router

| Destination | Action                      |
| ----------- | --------------------------- |
| Local       | Sent directly out interface |
| Remote      | Sent to default gateway     |

---

## 🚪 Default Gateway (DGW)

### What Is a Default Gateway?

A **router or Layer 3 switch** that forwards traffic off the local LAN.

Requirements:

* IP address in same network as hosts
* Can route to other networks

⚠️ No DGW or incorrect DGW → traffic **cannot leave the LAN**

---

### How Hosts Learn the Default Gateway

* **IPv4:** Static configuration or DHCP
* **IPv6:** Router Solicitation (RS) or manual config

📌 DGW is a **static last-resort route**

---

### Host Routing Tables

Commands:

* `route print`
* `netstat -r`

Routing table sections:

* Interface List
* IPv4 Routing Table
* IPv6 Routing Table

---

## 8.5 Introduction to Routing (Routers)

### Router Routing Table

Routers forward packets using a **routing table**.

Types of routes:

### 1️⃣ Directly Connected

* Automatically added
* Interface must be active and addressed

### 2️⃣ Remote Routes

* Learned:

  * **Statically** (manual)
  * **Dynamically** (routing protocols)

### 3️⃣ Default Route

* Used when no other match exists
* Often points toward ISP or upstream router

---

## 📌 Static Routing

Characteristics:

* Manually configured
* Manually updated
* Best for small, simple networks
* Often used for default routes

---

## 🔄 Dynamic Routing

Automatically:

* Discovers networks
* Updates routes
* Selects best path
* Adapts to topology changes

📌 Can advertise static default routes

---

## 📋 IPv4 Routing Table Codes (`show ip route`)

| Code | Meaning                    |
| ---- | -------------------------- |
| L    | Local interface address    |
| C    | Directly connected network |
| S    | Static route               |
| O    | OSPF                       |
| D    | EIGRP                      |
| S*   | Default route              |

📌 Router uses **longest prefix match**

---

## 🧠 Module 8 Key Takeaways

* IP is **connectionless, best effort, media independent**
* IPv4 uses a complex header; IPv6 simplifies it
* IPv6 eliminates NAT and expands address space
* Hosts decide: self, local, or remote
* Default gateway is required for off-LAN traffic
* Routing tables control packet forwarding
* Routers choose routes using **longest prefix match**
* Three route types: connected, remote, default

---

## 🔖 Tags (Obsidian)

```
#cisco #itn #ccna
#network-layer
#osi-layer-3
#ipv4 #ipv6
#routing
#default-gateway
#routing-table
#static-routing
#dynamic-routing
```

If you want next, I can:

* 🧠 Compare **IPv4 vs IPv6 (exam table)**
* 🧪 Create **routing-table practice questions**
* 🗺️ Walk through a **packet’s full path (L1–L7)**
* 🧩 Turn this into **atomic notes**
* 🔍 Explain **longest prefix match** with examples

Just say the word 👌