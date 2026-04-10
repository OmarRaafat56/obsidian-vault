[[CCNA]]
Module 7: Ethernet Switching
___

## 7.1 Ethernet Frames

Ethernet is the primary LAN technology, operating at both the Data Link (Layer 2) and Physical (Layer 1) layers. It is defined by IEEE 802.2 and 802.3 standards.
Data Link Sublayers

    LLC Sublayer (802.2): Communicates with the upper layers (Network Layer) and identifies which protocol is being used.

    MAC Sublayer (802.3): Handles data encapsulation (framing, addressing, error detection) and media access control.

#### Frame Characteristics

    Encapsulation: Includes Source/Destination MAC addresses and the Frame Check Sequence (FCS) for error detection.

    Frame Size: * Minimum: 64 bytes (Frames smaller than this are "runts" or "collision fragments" and are discarded).

        Maximum: 1518 bytes (Frames larger than 1500 bytes of data are "jumbo" or "baby giant" frames).
___

## 7.2 Ethernet MAC Address

A MAC address is a 48-bit (6-byte) binary value expressed as 12 hexadecimal digits.
Structure

    Organizationally Unique Identifier (OUI): The first 3 bytes (24 bits) assigned to the vendor by the IEEE.

    Vendor Assigned: The last 3 bytes (24 bits) assigned uniquely by the manufacturer.
___

#### Communication Types

| Type      | Destination MAC address         | Description                         |
| --------- | ------------------------------- | ----------------------------------- |
| Unicast   | Unique address of the NIC       | Sent to one specific device.        |
| Broadcast | FF-FF-FF-FF-FF-FF               | Sent to all devices in the LAN      |
| Multicast | 01-00-5E (IPv4) or 33-33 (IPv6) | Sent to a specific group of devices |
___


## 7.3 The MAC Address Table

* Switches use a MAC Address Table (also known as a CAM Table) to make forwarding decisions.

    * Learn: The switch examines the Source MAC address of incoming frames. If it's new, the switch maps that MAC to the port it arrived on.

    * Forward: The switch looks at the Destination MAC.

        If found in the table, the frame is sent out the specific port (Filtering).

        If NOT found (Unknown Unicast), or if it is a Broadcast/Multicast, the frame is Flooded out all ports except the one it arrived on.
___

## 7.4 Switch Speeds and Forwarding Methods

#### Forwarding Methods

    Store-and-Forward: Receives the entire frame and checks the CRC (error check) before forwarding. Required for QoS.

    Cut-Through: Forwards the frame as soon as the destination address is read.

        Fast-forward: Lowest latency; no error checking.

        Fragment-free: Checks the first 64 bytes (where most collisions occur) before forwarding.
___

#### Memory Buffering

    Port-based: Frames are stored in queues assigned to specific ports.

    Shared Memory: All frames are stored in a common buffer, dynamically allocated to ports as needed.
___

#### Duplex and Speed

    Full-Duplex: Simultaneous send/receive (Standard on modern switches).

    Half-Duplex: One-way communication at a time (Legacy/Hubs).

    Auto-MDIX: Automatically detects the cable type (straight-through vs. crossover) and configures the port accordingly.
___

Tags

#Cisco #CCNA #Networking #Ethernet #Layer2 #Switching #MACAddress #ITN

