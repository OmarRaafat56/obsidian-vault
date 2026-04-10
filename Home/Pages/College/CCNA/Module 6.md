[[CCNA]]


---

# Module 6 – Data Link Layer

**Course:** Introduction to Networks (ITN v7.0)
**Module Objective:** Explain how **media access control** in the data link layer supports communication across networks.

---

## 🧱 Purpose of the Data Link Layer (Layer 2)

### What the Data Link Layer Does

The **Data Link Layer** is responsible for **node-to-node delivery** of data on the same network medium.

Key responsibilities:

* Enables communication **between Network Interface Cards (NICs)**
* Encapsulates **Layer 3 packets (IPv4/IPv6)** into **Layer 2 frames**
* Controls access to the physical media
* Performs **error detection** and discards corrupted frames

📌 This layer prepares data so it can be transmitted safely across the physical layer.

---

## 🧩 IEEE 802 Data Link Sublayers

The Data Link Layer is divided into **two sublayers**:

### 1️⃣ Logical Link Control (LLC)

* Communicates with **upper layers (Layer 3 and above)**
* Identifies which **network layer protocol** is being used
* Separates networking software from hardware

### 2️⃣ Media Access Control (MAC)

* Responsible for **data encapsulation**
* Controls how devices **access the media**
* Handles **physical addressing (MAC addresses)**

---

## 🔁 Data Link Layer at Each Hop

When data travels across multiple networks, **Layer 2 is rebuilt at every hop**.

At each router:

1. Accepts a frame
2. Removes the Layer 2 frame
3. Re-encapsulates the packet into a new frame
4. Forwards it on the next network segment

📌 **Layer 2 addresses change at every hop**
📌 **Layer 3 addresses remain the same end-to-end**

---

## 🏗️ Data Link Layer Standards

Defined by international standards organizations:

* **IEEE**
* **ITU**
* **ISO**
* **ANSI**

---

## 6.2 Network Topologies

### Physical vs Logical Topology

| Type     | Description                                    |
| -------- | ---------------------------------------------- |
| Physical | Physical layout of devices and cables          |
| Logical  | How data flows using interfaces and addressing |

---

## 🌐 WAN Topologies

### Common WAN Physical Topologies

* **Point-to-Point**

  * Direct link between two devices
  * Simple and efficient
* **Hub-and-Spoke**

  * Central hub connects multiple branches
* **Mesh**

  * Every device connects to every other
  * High redundancy, high cost

---

### Point-to-Point WAN

* Two nodes only
* No shared media
* Simple Layer 2 protocols (PPP, HDLC)

---

## 🖧 LAN Topologies

### Modern LANs

* **Star topology**
* **Extended star topology**
* Easy to install, scalable, and troubleshoot

### Legacy LAN Topologies

* **Bus** – shared cable with terminators
* **Ring** – devices connected in a circular path

---

## 🔄 Half-Duplex vs Full-Duplex

| Mode        | Description                     | Used By     |
| ----------- | ------------------------------- | ----------- |
| Half-duplex | Send or receive (not both)      | WLANs, hubs |
| Full-duplex | Send and receive simultaneously | Switches    |

📌 Collisions only occur in **half-duplex**

---

## 🚦 Media Access Control Methods

### Contention-Based Access

* Devices compete for the medium
* Operates in **half-duplex**
* Examples:

  * **CSMA/CD** (Ethernet – legacy)
  * **CSMA/CA** (Wireless LANs)

### Controlled Access

* Deterministic (scheduled access)
* No collisions
* Used by legacy technologies:

  * Token Ring
  * ARCNET

---

## ⚔️ CSMA/CD (Collision Detection)

Used in **legacy Ethernet LANs**:

1. Device listens before transmitting
2. Collision occurs if two transmit simultaneously
3. Devices detect collision
4. Wait a random time
5. Retransmit

📌 Obsolete due to full-duplex switching

---

## 🛡️ CSMA/CA (Collision Avoidance)

Used in **WLANs (802.11)**:

* Devices announce transmission duration
* Other devices wait until medium is free
* Prevents collisions before they occur

📌 Wireless **cannot detect collisions**, only avoid them

---

## 6.3 Data Link Frame

### What Is a Frame?

A **frame** is the Layer 2 data unit created by encapsulating a packet with:

* **Header**
* **Data**
* **Trailer**

---

### Frame Fields and Functions

| Field            | Purpose                              |
| ---------------- | ------------------------------------ |
| Frame Start/Stop | Identifies frame boundaries          |
| Addressing       | Source and destination MAC addresses |
| Type             | Identifies Layer 3 protocol          |
| Control          | Flow control information             |
| Data             | Encapsulated packet                  |
| Error Detection  | Detects transmission errors (FCS)    |

---

## 🆔 Layer 2 Addresses (MAC Addresses)

* Physical (hardware) addresses
* Used for **local delivery only**
* Contained in the frame header
* **Updated at every hop**

📌 MAC addresses ≠ IP addresses

---

## 🧵 LAN and WAN Frame Types

Frame format depends on:

* Logical topology
* Physical media

Common Layer 2 protocols:

* **Ethernet**
* **802.11 Wireless**
* **PPP**
* **HDLC**
* **Frame Relay**

---

## 🧠 Module 6 Key Takeaways

* Layer 2 prepares data for the physical network
* Handles NIC-to-NIC communication
* Uses **LLC and MAC sublayers**
* Frames are rebuilt at every hop
* Topologies can be physical or logical
* CSMA/CD = Ethernet (legacy)
* CSMA/CA = Wireless
* Frames contain header, data, and trailer
* MAC addresses are used only for local delivery

---

## 🔖 Tags (Obsidian)


#cisco #itn #ccna
#data-link-layer
#osi-layer-2
#mac-address
#ethernet #wlan
#csma-cd #csma-ca
#network-topologies



