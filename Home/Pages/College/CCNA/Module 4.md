[[CCNA]]


---

# Module 4 – Physical Layer

**Course:** Introduction to Networks (ITN v7.0)
**Module Objective:** Explain how physical layer protocols, services, and network media support communication across data networks.

---

## Purpose of the Physical Layer

* Establishes the **physical connection** between devices
* Connection can be **wired or wireless**
* Uses a **Network Interface Card (NIC)** to connect devices to the network
* Performance varies depending on media and technology

### Core Functions

* Transports **raw bits (0s and 1s)** across the network medium
* Accepts frames from the **Data Link Layer**
* Encodes frames into **signals**
* Final step of the **encapsulation process**
* Receiving device decodes bits and re-encapsulates data

---

## Physical Layer Characteristics

Physical layer standards define **how data is physically transmitted** and cover three areas:

### 1. Physical Components

* Hardware devices
* Network interfaces
* Connectors
* Cabling types and materials

### 2. Encoding

* Converts bits into recognizable patterns
* Ensures synchronization between devices
* Common encoding methods:

  * Manchester
  * 4B/5B
  * 8B/10B

### 3. Signaling

* Represents bits on the medium
* Depends on media type:

  * Electrical signals → copper
  * Light pulses → fiber
  * Radio/microwave → wireless

---

## Bandwidth Concepts

### Bandwidth

* Maximum data capacity of a medium
* Measured in **bits per second (bps)**

| Unit | Meaning  |
| ---- | -------- |
| Kbps | 10³ bps  |
| Mbps | 10⁶ bps  |
| Gbps | 10⁹ bps  |
| Tbps | 10¹² bps |

### Performance Metrics

* **Latency:** Time for data to travel from source to destination
* **Throughput:** Actual data transferred per unit time
* **Goodput:** Useful data transferred

  * `Goodput = Throughput – overhead`

---

## Copper Cabling

### Characteristics

* Most common network cabling
* Inexpensive and easy to install
* Low resistance to electrical flow

### Limitations

* **Attenuation:** Signal weakens over distance
* **Interference:**

  * EMI (Electromagnetic Interference)
  * RFI (Radio Frequency Interference)
  * Crosstalk

### Mitigation Techniques

* Follow cable length limits
* Use shielding and grounding
* Twist wire pairs

---

## Types of Copper Cabling

### Unshielded Twisted Pair (UTP)

* Most common Ethernet cable
* Uses **RJ-45 connectors**
* Four twisted wire pairs
* No shielding

**Interference Protection**

* Cancellation (opposite polarity)
* Different twist rates per pair

### Shielded Twisted Pair (STP)

* Extra shielding for EMI/RFI protection
* More expensive and harder to install
* Uses RJ-45 connectors

### Coaxial Cable

* Central copper conductor
* Insulation + shielding
* Used for:

  * Cable internet
  * Wireless antenna connections

---

## UTP Cabling Standards

* Defined by **TIA/EIA 568**

  * Cable types
  * Length limits
  * Termination
  * Testing
* Electrical performance defined by **IEEE**

### Common Categories

* Cat 3
* Cat 5 / 5e
* Cat 6

---

## UTP Cable Types

| Cable Type       | Wiring                     | Use Case                 |
| ---------------- | -------------------------- | ------------------------ |
| Straight-through | Same standard on both ends | Host → Switch            |
| Crossover        | T568A ↔ T568B              | Switch ↔ Switch (legacy) |
| Rollover         | Cisco proprietary          | Console access           |

> Note: Most modern NICs use **Auto-MDIX**, making crossover cables mostly obsolete.

---

## Fiber-Optic Cabling

### Key Properties

* Uses **light pulses** instead of electricity
* Extremely high bandwidth
* Very long distances
* Immune to EMI/RFI
* Made of thin glass fibers

### Advantages

* Higher speed
* Longer range
* Electrical isolation
* Better security

---

## Types of Fiber

### Single-Mode Fiber (SMF)

* Very small core
* Uses lasers
* Long-distance communication

### Multimode Fiber (MMF)

* Larger core
* Uses LEDs
* Up to **10 Gbps over 550 meters**
* More dispersion than SMF

---

## Fiber Usage Scenarios

* Enterprise network backbones
* Fiber-to-the-Home (FTTH)
* Long-haul service provider networks
* Submarine cables

---

## Fiber-Optic Connectors & Cables

### Connectors

* ST
* SC
* LC
* Duplex LC

### Patch Cords

* Yellow jacket → Single-mode
* Orange/Aqua → Multimode

---

## Fiber vs Copper Comparison

| Feature            | UTP           | Fiber          |
| ------------------ | ------------- | -------------- |
| Bandwidth          | Up to 10 Gbps | Up to 100 Gbps |
| Distance           | 1–100 m       | Up to 100 km   |
| EMI/RFI            | Susceptible   | Immune         |
| Cost               | Low           | High           |
| Installation Skill | Low           | High           |
| Safety             | Low           | High           |

---

## Wireless Media

### Properties

* Uses radio or microwave signals
* Provides mobility
* Increasingly common

### Limitations

* Limited coverage
* Susceptible to interference
* Security risks
* Shared medium (half-duplex)

---

## Wireless Standards

* **Wi-Fi (802.11):** Wireless LAN
* **Bluetooth (802.15):** WPAN
* **WiMAX (802.16):** Broadband wireless
* **Zigbee (802.15.4):** Low-power IoT networks

---

## Wireless LAN (WLAN)

### Required Components

* Wireless Access Point (AP)
* Wireless NICs

### Key Notes

* Standards compatibility is critical
* Strong security policies required
* Wireless expands attack surface

---

## Module Takeaways

* Physical layer enables **all network communication**
* Defines hardware, signaling, and encoding
* Copper, fiber, and wireless each have trade-offs
* Fiber dominates backbone networks
* Wireless prioritizes mobility but introduces risks

---

## Tags


#networking #physical-layer #cisco-itn
#osi-model #cabling #utp #fiber-optic
#wireless #bandwidth #encoding #signaling
#ethernet #wlan #network-media


If you want next:

* **Exam-focused flash notes**
* **OSI-layer comparison table**
* **Visual-friendly cheat sheet**
* Or **split this into atomic Obsidian notes with backlinks**