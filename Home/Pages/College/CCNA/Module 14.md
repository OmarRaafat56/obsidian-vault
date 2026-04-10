[[CCNA]]
Here’s a structured **Obsidian-ready summary** of your Module 14 notes with headings, bullet points, and relevant tags:

---

# Module 14: Transport Layer

**Source:** Introduction to Networks v7.0 (Cisco ITN)
**Objective:** Compare the operations of transport layer protocols in supporting end-to-end communication.

---

## 📝 Module Topics

* **Transportation of Data** – Purpose of the transport layer in end-to-end communication.
* **TCP Overview** – Characteristics and operation of TCP.
* **UDP Overview** – Characteristics and operation of UDP.
* **Port Numbers** – Role of port numbers in TCP/UDP communication.
* **TCP Communication Process** – Session establishment, termination, and reliability.
* **Reliability and Flow Control** – How TCP ensures ordered and reliable delivery.
* **UDP Communication** – How UDP manages communication with low overhead.

---

## 🚚 Transport Layer Overview

**Role:**

* Provides logical communication between applications on different hosts.
* Connects application layer to lower network layers.

**Responsibilities:**

* Track individual conversations.
* Segment and reassemble data.
* Add header information.
* Separate and manage multiple conversations.
* Use segmentation and multiplexing for concurrent communications.

**Protocols:**

* **TCP** – Connection-oriented, reliable, ordered delivery, flow control.
* **UDP** – Connectionless, best-effort, low overhead, minimal error checking.

---

## TCP Overview

**Features:**

* Connection-oriented (establishes a session).
* Ensures reliable delivery.
* Guarantees same-order delivery.
* Supports flow control.

**TCP Header Fields:**

| Field                 | Size   | Purpose                             |
| --------------------- | ------ | ----------------------------------- |
| Source Port           | 16-bit | Identifies source application       |
| Destination Port      | 16-bit | Identifies destination application  |
| Sequence Number       | 32-bit | For reassembly                      |
| Acknowledgment Number | 32-bit | Indicates next expected byte        |
| Header Length         | 4-bit  | TCP header length                   |
| Reserved              | 6-bit  | Future use                          |
| Control Bits          | 6-bit  | Flags: URG, ACK, PSH, RST, SYN, FIN |
| Window Size           | 16-bit | Flow control                        |
| Checksum              | 16-bit | Error checking                      |
| Urgent                | 16-bit | Urgent data indicator               |

**Applications Using TCP:**

* Web browsing, email, file transfer, and any app requiring reliability.

---

## UDP Overview

**Features:**

* Connectionless, low overhead.
* No acknowledgment or retransmission.
* Data reconstructed in received order.

**UDP Header Fields:**

| Field            | Size   | Purpose                            |
| ---------------- | ------ | ---------------------------------- |
| Source Port      | 16-bit | Identifies source application      |
| Destination Port | 16-bit | Identifies destination application |
| Length           | 16-bit | Datagram length                    |
| Checksum         | 16-bit | Error checking                     |

**Applications Using UDP:**

* Live video/VoIP (tolerates data loss).
* DNS, DHCP (simple request/reply).
* SNMP, TFTP (applications handle reliability).

---

## Port Numbers

**Purpose:**

* Manage multiple simultaneous communications.
* Source port → originating application.
* Destination port → target application.

**Socket:** Combination of IP address + port number for each endpoint.

**Port Number Ranges:**

| Type            | Range       | Use                                                     |
| --------------- | ----------- | ------------------------------------------------------- |
| Well-Known      | 0–1023      | Common services (HTTP, FTP, SMTP, DNS)                  |
| Registered      | 1024–49151  | Assigned to user applications (e.g., Cisco RADIUS 1812) |
| Private/Dynamic | 49152–65535 | Assigned by OS for client applications                  |

**Important Ports:**

* 20/21 TCP – FTP
* 22 TCP – SSH
* 23 TCP – Telnet
* 25 TCP – SMTP
* 53 TCP/UDP – DNS
* 67/68 UDP – DHCP
* 69 UDP – TFTP
* 80 TCP – HTTP
* 443 TCP – HTTPS
* 161 UDP – SNMP

**Tool:** `netstat` – Verifies active TCP connections for security auditing.

---

## TCP Communication Process

**Server Processes:**

* Server applications assigned to unique port numbers.
* Accept segments addressed to correct socket.

**Connection Establishment (Three-Way Handshake):**

1. Client sends SYN to server.
2. Server replies SYN-ACK.
3. Client responds with ACK.

**Session Termination:**

1. Client sends FIN.
2. Server ACKs FIN.
3. Server sends FIN.
4. Client ACKs FIN.

**Control Flags:** URG, ACK, PSH, RST, SYN, FIN

---

## Reliability and Flow Control (TCP)

**Reliable Delivery:**

* Segments tracked via sequence numbers.
* Lost segments retransmitted (SACK optional).
* Ensures data reassembled in correct order.

**Flow Control:**

* Window size indicates how much data can be received.
* Adjusts sender rate to match receiver capacity.

**Maximum Segment Size (MSS):**

* Default 1,460 bytes (Ethernet MTU 1,500 – IP/TCP headers 40).

**Congestion Avoidance:**

* TCP detects and mitigates network congestion with timers and algorithms.

---

## UDP Communication

**Low Overhead:**

* No connection establishment.
* No tracking or reordering of segments.

**Server/Client Processes:**

* Server uses well-known/registered ports.
* Client dynamically selects source port; uses server’s port as destination.
* Same port pair used for entire conversation.

---

## ✅ Module Summary

* Transport layer links application and network layers.
* TCP ensures reliability, ordering, and flow control.
* UDP is lightweight, connectionless, used for time-sensitive apps.
* Port numbers enable multiple simultaneous conversations.
* TCP uses sequence numbers, sliding windows, and congestion control.
* UDP simply forwards datagrams as received, leaving reliability to applications.

---

## 🏷️ Tags

#Networking #TransportLayer #TCP #UDP #PortNumbers #FlowControl #Reliability #CiscoITN #NetworkProtocols #EndToEndCommunication

---

If you want, I can also create a **visual Obsidian-style map** linking TCP, UDP, ports, reliability, and flow control—it would make this module even easier to memorize.

Do you want me to make that?