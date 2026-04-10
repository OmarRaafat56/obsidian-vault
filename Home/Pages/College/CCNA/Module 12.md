[[CCNA]]
Perfect — I’ve got you 👍
Here’s a **clean, CCNA-aligned, Obsidian-ready summary** of **Module 12: IPv6 Addressing (ITN v7.0)**, matching the **style, depth, and structure** of your earlier modules.

---

# Module 12 – IPv6 Addressing

**Course:** Introduction to Networks (ITN v7.0)
**Module Objective:** Implement an **IPv6 addressing scheme**

---

## 12.1 IPv4 Issues

### Why IPv6 Is Needed

* IPv4 provides ~**4.3 billion** addresses → **exhausted**
* NAT introduced complexity and breaks end-to-end connectivity
* Growth of:

  * Internet users
  * Mobile devices
  * IoT
* IPv6 uses **128-bit addresses**, providing a vastly larger address space

---

## IPv4 and IPv6 Coexistence

IPv4 and IPv6 will **coexist for many years**.

### IPv6 Transition Techniques

| Method          | Description                                          |
| --------------- | ---------------------------------------------------- |
| **Dual Stack**  | Devices run IPv4 and IPv6 simultaneously             |
| **Tunneling**   | IPv6 packets encapsulated inside IPv4 packets        |
| **Translation** | NAT64 allows IPv6-only to communicate with IPv4-only |

📌 **Goal:** Native IPv6 end-to-end
📌 Tunneling and translation are **temporary solutions**

---

## 12.2 IPv6 Address Representation

### IPv6 Address Format

* **128 bits**, written in **hexadecimal**
* Preferred format:

  ```
  x:x:x:x:x:x:x:x
  ```
* Each `x` = **16 bits (4 hex digits)** → called a **hextet**
* Not case-sensitive

---

### Rule 1 – Omit Leading Zeros

Only **leading zeros** can be removed.

```
0db8 → db8
0000 → 0
```

Example:

```
2001:0db8:0000:1111:0000:0000:0000:0200
↓
2001:db8:0:1111:0:0:0:200
```

---

### Rule 2 – Double Colon (::)

* Replaces **one contiguous group** of all-zero hextets
* Can be used **once per address only**

Example:

```
2001:db8:cafe:1:0:0:0:1
↓
2001:db8:cafe:1::1
```

---

## 12.3 IPv6 Address Types

### Three IPv6 Address Categories

| Type          | Purpose                                 |
| ------------- | --------------------------------------- |
| **Unicast**   | Identifies a single interface           |
| **Multicast** | One-to-many communication               |
| **Anycast**   | One-to-nearest (shared unicast address) |

📌 IPv6 has **no broadcast addresses**

---

## IPv6 Prefix Length

* Written using **slash notation**
* Range: `/0` to `/128`
* **/64 is strongly recommended** for LANs

📌 SLAAC **requires a 64-bit interface ID**

---

## IPv6 Unicast Address Types

### Global Unicast Address (GUA)

* Public, globally routable
* Assigned from **2000::/3**
* Begins with **2 or 3**

### Link-Local Address (LLA)

* Required on **every IPv6 interface**
* Used only on the **local link**
* **Not routable**
* Range: `fe80::/10`

📌 Devices typically have **both a GUA and an LLA**

---

## IPv6 GUA Structure

```
| Global Routing Prefix | Subnet ID | Interface ID |
```

* **Global Routing Prefix** – Assigned by ISP
* **Subnet ID** – Used to create internal subnets
* **Interface ID** – Host portion (typically 64 bits)

📌 IPv6 allows:

* All-zeros host
* All-ones host
  (unlike IPv4)

---

## 12.4 Static GUA and LLA Configuration

### Static GUA on a Router

```plaintext
R1(config)# interface g0/0/0
R1(config-if)# ipv6 address 2001:db8:acad:1::1/64
R1(config-if)# no shutdown
```

📌 `ipv6` replaces `ip` in IOS commands

---

### Static IPv6 on a Host

* Configured similarly to IPv4
* **Best practice:** Use the router’s **LLA** as the default gateway

📌 With SLAAC or DHCPv6, the router LLA is **automatically learned**

---

### Static Link-Local Address (LLA)

```plaintext
R1(config)# interface g0/0/0
R1(config-if)# ipv6 address fe80::1:1 link-local
```

📌 LLAs must be **unique per link**, not per network
📌 Common to use different LLAs per router interface

---

## 12.5 Dynamic Addressing for IPv6 GUAs

### ICMPv6 Messages

| Message | Purpose                                    |
| ------- | ------------------------------------------ |
| **RS**  | Sent by hosts to discover routers          |
| **RA**  | Sent by routers to provide addressing info |

RA messages include:

* Network prefix
* Prefix length
* Default gateway
* DNS info
* Addressing method

---

## IPv6 GUA Configuration Methods

### Method 1 – SLAAC

* No DHCPv6 required
* Router provides prefix
* Host creates interface ID using:

  * **EUI-64**
  * **Random 64-bit value**

---

### Method 2 – SLAAC + Stateless DHCPv6

* SLAAC → GUA
* Router LLA → Default gateway
* Stateless DHCPv6 → DNS, domain name

---

### Method 3 – Stateful DHCPv6

* DHCPv6 assigns:

  * GUA
  * Prefix length
  * DNS
* Router LLA still used as default gateway

---

## EUI-64 vs Random Interface IDs

### EUI-64 Process

* Insert `fffe` into MAC address
* Flip the **7th bit**

Example:

```
MAC: fc:99:47:75:ce:e0
EUI-64: fe:99:47:ff:fe:75:ce:e0
```

---

### Random Interface IDs

* Used by modern OSs (e.g., Windows Vista+)
* Improves **privacy**
* Still requires **Duplicate Address Detection (DAD)**

---

## 12.6 Dynamic IPv6 LLAs

* Every IPv6 interface **must** have an LLA
* Can be:

  * Manually configured
  * Dynamically generated

### Cisco Routers

* Automatically generate LLAs
* Use **EUI-64 by default**

```plaintext
show ipv6 interface brief
```

---

## 12.7 IPv6 Multicast Addresses

### Multicast Prefix

```
ff00::/8
```

📌 Multicast addresses are **destination-only**

---

### Well-Known IPv6 Multicast Addresses

| Address     | Purpose          |
| ----------- | ---------------- |
| **ff02::1** | All IPv6 nodes   |
| **ff02::2** | All IPv6 routers |

📌 Routers join `ff02::2` when `ipv6 unicast-routing` is enabled

---

### Solicited-Node Multicast

* Similar to all-nodes multicast
* Maps to a special Ethernet multicast MAC
* Used by **Neighbor Discovery**
* Improves efficiency by reducing unnecessary processing

---

## 12.8 Subnet an IPv6 Network

### IPv6 Subnetting Basics

* Subnetting uses the **Subnet ID**
* Located between:

  * Global Routing Prefix
  * Interface ID

---

### IPv6 Subnetting Example

Given:

```
2001:db8:acad::/48
```

* 16-bit Subnet ID
* **65,536 /64 subnets**
* Subnet ID increments in **hexadecimal**

---

### Router IPv6 Subnet Configuration

```plaintext
R1(config)# interface g0/0/0
R1(config-if)# ipv6 address 2001:db8:acad:1::1/64

R1(config)# interface g0/0/1
R1(config-if)# ipv6 address 2001:db8:acad:2::1/64

R1(config)# interface s0/1/0
R1(config-if)# ipv6 address 2001:db8:acad:3::1/64
```

---

## 🧠 Module 12 Key Takeaways

* IPv6 solves IPv4 address exhaustion
* IPv4 and IPv6 coexist via dual stack, tunneling, and translation
* IPv6 addresses are 128-bit hexadecimal values
* Use `/64` for most networks
* Devices typically have both a **GUA and an LLA**
* LLAs are required and not routable
* GUAs can be statically or dynamically assigned
* RA messages control IPv6 address configuration
* Multicast replaces broadcast in IPv6
* IPv6 subnetting is simple and scalable

---

## 🔖 Tags (Obsidian)

```
#cisco #ccna #itn
#ipv6
#ipv6-addressing
#slaac #dhcpv6
#link-local
#multicast
#ipv6-subnetting
```

If you want next, I can:

* 🧪 Build **IPv6 subnetting practice**
* 📋 Create a **SLAAC vs DHCPv6 comparison sheet**
* 🧠 Make **exam trap notes** (RA flags, LLAs, multicast)
* 🖥️ Walk through **Packet Tracer IPv6 labs**
* 🗂 Split this into **atomic Obsidian notes**

Just tell me what’s next 🚀