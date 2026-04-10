[[CCNA]]
Locked in — **same deal, same quality** 😄
Here’s a **clear, CCNA-ready, Obsidian-friendly summary** of **Module 10: Basic Router Configuration (ITN v7.0)**, matching your previous modules in structure, depth, and exam focus.

---

# Module 10 – Basic Router Configuration

**Course:** Introduction to Networks (ITN v7.0)
**Module Objective:** Implement **initial settings** on a router and **end devices**.

---

## 10.1 Configure Initial Router Settings

### Purpose

Before a router can forward traffic, it must be:

* Identified
* Secured
* Accessible
* Saved

---

## 🛠️ Basic Router Configuration Tasks

### Required Initial Tasks

* Configure **device name**
* Secure **privileged EXEC mode**
* Secure **user EXEC mode**
* Secure **remote access (Telnet / SSH)**
* Encrypt plaintext passwords
* Configure a **banner message**
* Save the configuration to **NVRAM**

---

## 🧾 Core IOS Configuration Commands

```plaintext
Router(config)# hostname R1
Router(config)# enable secret password

Router(config)# line console 0
Router(config-line)# password password
Router(config-line)# login

Router(config)# line vty 0 4
Router(config-line)# password password
Router(config-line)# login
Router(config-line)# transport input ssh telnet

Router(config)# service password-encryption
Router(config)# banner motd # Unauthorized access prohibited #
Router(config)# end
Router# copy running-config startup-config
```

📌 `enable secret` is **encrypted** (preferred over `enable password`)
📌 `service password-encryption` encrypts **plaintext passwords only**

---

## 🧠 Privileged vs User EXEC

| Mode            | Prompt | Purpose             |
| --------------- | ------ | ------------------- |
| User EXEC       | `>`    | Limited monitoring  |
| Privileged EXEC | `#`    | Full device control |

---

## 10.2 Configure Router Interfaces

### Why Interfaces Matter

* Routers are **unreachable** unless interfaces are:

  * Configured
  * Enabled
  * Physically connected

---

## 🔌 Interface Configuration Steps

```plaintext
Router(config)# interface type number
Router(config-if)# description description-text
Router(config-if)# ip address ipv4-address subnet-mask
Router(config-if)# ipv6 address ipv6-address/prefix
Router(config-if)# no shutdown
```

📌 Interfaces are **shutdown by default**

---

## 🧪 Interface Configuration Example (R1)

### GigabitEthernet0/0/0 – LAN

```plaintext
R1(config)# interface g0/0/0
R1(config-if)# description Link to LAN
R1(config-if)# ip address 192.168.10.1 255.255.255.0
R1(config-if)# ipv6 address 2001:db8:acad:10::1/64
R1(config-if)# no shutdown
```

### GigabitEthernet0/0/1 – WAN

```plaintext
R1(config)# interface g0/0/1
R1(config-if)# description Link to R2
R1(config-if)# ip address 209.165.200.225 255.255.255.252
R1(config-if)# ipv6 address 2001:db8:feed:224::1/64
R1(config-if)# no shutdown
```

📌 Interface state messages:

* **Link up/down** → Physical layer
* **Line protocol up/down** → Data link layer

---

## 🔍 Verifying Interface Configuration

### Quick Status Checks

```plaintext
show ip interface brief
show ipv6 interface brief
```

Displays:

* Interface
* IP address
* Administrative status
* Line protocol status

---

### Routing Table Verification

```plaintext
show ip route
show ipv6 route
```

📌 Directly connected routes appear automatically once interfaces are up

---

### Detailed Interface Statistics

```plaintext
show interfaces
show ip interface g0/0/0
show ipv6 interface g0/0/0
```

Used to verify:

* MTU
* Duplex/speed
* Errors
* IPv4 / IPv6 settings

---

## 10.3 Configure the Default Gateway

---

## 🚪 Default Gateway on a Host

### What Is the Default Gateway?

* Used when sending traffic to **another network**
* Typically the **router interface IP** on the local LAN

📌 Host IP and router interface IP **must be in the same network**

---

### Example

* PC1 → PC3 (remote)
* Packet destination IP = PC3
* Frame destination MAC = **default gateway**

---

## 🖧 Default Gateway on a Switch

### Why Switches Need a Default Gateway

* Required for **remote management** (SSH, Telnet, ping)
* Not used for frame forwarding

### Configuration Command

```plaintext
Switch(config)# ip default-gateway ip-address
```

📌 Applies only to **Layer 2 switches**

---

## 🧪 Packet Tracer Skills Practiced

* Initial router configuration
* Interface configuration
* Connectivity verification
* Default gateway troubleshooting
* Physical vs logical connectivity

---

## 🧠 Module 10 Key Takeaways

* Routers require **initial security configuration**
* Interfaces must be:

  * Addressed
  * Enabled (`no shutdown`)
  * Physically connected
* Use `show ip interface brief` for quick checks
* Routing tables populate automatically for connected networks
* End devices require a **default gateway** to reach remote networks
* Switches need a default gateway for **remote management**
* Always save configs to **startup-config**

---

## 🔖 Tags (Obsidian)

```
#cisco #itn #ccna
#basic-router-configuration
#ios-commands
#router-interfaces
#default-gateway
#show-commands
#ipv4 #ipv6
```

If you want next, I can:

* 🧪 Build **CLI practice labs**
* 📋 Create a **router setup checklist**
* 🔍 Do **common exam traps** (shutdown interfaces, wrong DGW)
* 🧠 Compare **router vs switch configuration**
* 🗂 Convert this into **atomic Obsidian notes**

Just say the word 👌