[[Networks 2]]

---

# 📡 Software Defined Networks (SDN) – Applications

## 🧠 Overview

* **SDN applications** run **above the SDN controller**
* Communicate via the **northbound API**
* Responsible for defining and managing **flow rules** on network devices

---

## 🔌 Controller API Capabilities

Through the controller’s API, SDN applications can:

* 📍 Route traffic through optimal paths
* ⚖️ Perform **load balancing** across multiple paths/endpoints
* 🔄 Adapt to **topology changes** (failures, new devices)
* 🔐 Redirect traffic for:

  * Inspection
  * Authentication
  * Security enforcement

---

## ⚙️ SDN Application Responsibilities

* Implement network services:

  * Load balancing
  * Firewalling
* Operate in an **event-driven manner**
* React to:

  * Controller events
  * External inputs

---

## 🔔 Events Handled by SDN Applications

### 1. Device Discovery Events

* **End-user devices** (PCs, phones, printers)
* **Network devices** (switches, routers, APs)

### 2. Incoming Packet Events

Triggered when:

* A flow rule sends packets to the controller
* No matching flow entry exists

👉 Default behavior:

* Forward packet to controller (or drop, depending on policy)

---

## 🔄 Alternate SDN Implementation Approaches

### 1. SDN via APIs

#### 📌 Concept

* Uses built-in device functions accessible remotely
* Often implemented via **REST APIs**

#### 🧩 API Levels

* Device level
* Controller level
* Policy level

#### ✅ Benefits

* Works with **legacy devices**
* No need for OpenFlow upgrades
* Enables automation & orchestration

#### ❌ Limitations

* No centralized controller abstraction
* Developers must manage **individual devices**
* APIs may be **non-standard**
* Must coordinate with distributed control planes

---

### 2. SDN via Hypervisor-Based Overlay Networks

#### 📌 Concept

* Builds **virtual networks on top of physical infrastructure**
* Common in **virtualized data centers**

#### 🧱 Key Features

* Network controlled at the **edge (hypervisors)**
* Underlying network is abstracted
* Uses **tunneling (encapsulation)**

---

## 🌐 VXLAN (Virtual Extensible LAN)

### 🧩 Basics

* Encapsulates **Layer 2 frames inside Layer 3 packets**
* Uses **MAC-in-IP tunneling**
* Developed by VMware & Cisco

### 🔢 Key Characteristics

* 24-bit VNI → ~16 million segments
* Each segment = isolated virtual network
* Endpoints = **VTEPs (VXLAN Tunnel Endpoints)**

---

## 🔌 VTEP (VXLAN Tunnel Endpoint)

* Edge device of VXLAN network
* Performs:

  * **Encapsulation** (source)
  * **Decapsulation** (destination)
* Can be:

  * Physical switch
  * Virtual switch (hypervisor)

---

## 📦 VXLAN Packet Structure

* **Outer IP Header** → identifies VTEPs
* **Outer MAC Header** → next-hop delivery
* **VXLAN Header (8 bytes)**:

  * VNI (24-bit identifier)
  * Flags (validity)
  * Reserved fields

---

## 🔄 VXLAN vs VLAN

| Feature      | VLAN    | VXLAN       |
| ------------ | ------- | ----------- |
| Max networks | ~4,096  | ~16 million |
| Scalability  | Limited | Very high   |
| Flexibility  | Low     | High        |
| Isolation    | Basic   | Advanced    |

---

## ✅ Benefits of VXLAN

* Massive scalability
* Flexible virtual network creation
* Centralized management
* Improved security via isolation

---

## ⚖️ Comparison of SDN Approaches

| Criterion               | Open SDN | SDN via APIs | Overlay SDN |
| ----------------------- | -------- | ------------ | ----------- |
| Plane separation        | High     | Low          | Medium      |
| Device simplification   | High     | Low          | Medium      |
| Required changes        | Low      | High         | Medium      |
| Single point of failure | Low      | Medium       | N/A         |
| Deep packet inspection  | Low      | Low          | Medium      |

---

## 🧪 Examples of Overlay SDN Solutions

* VMware NSX
* Juniper Junos Contrail
* IBM SDN for Virtual Environments

---

# 🏷️ Tags

#SDN #SDNApplications #Networking #NetworkAutomation #OverlayNetworks #VXLAN #VLAN #CloudNetworking #Virtualization #DataCenter #NetworkSecurity #RESTAPI #SDNArchitecture #VTEP #Encapsulation #LoadBalancing #Firewall #NetworkEngineering
