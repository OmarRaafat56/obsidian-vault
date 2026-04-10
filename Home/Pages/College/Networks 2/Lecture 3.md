[[Networks 2]]

---

# 📡 Software Defined Networks (SDN)

## 🧠 SDN Controller

The **SDN controller** acts as the central “brain” of the network:

* Abstracts underlying network devices
* Provides a simplified view of network resources to applications
* Enables programmability and centralized control

### 🔑 Key Functions

* Define and manage **network flows**
* Handle packets forwarded by devices
* Maintain **per-flow statistics**
* Hide device-specific implementation details
* Support modular (pluggable) architecture

---

## ⚙️ Core Modules of SDN Controller

### 🔍 Discovery

* **End-user device discovery** (laptops, phones, printers)
* **Network device discovery** (switches, routers, APs)

### 🌐 Topology Management

* Maintains network structure and interconnections

### 🔄 Flow Management

* Tracks flows in a database
* Synchronizes flow rules across devices

---

## 🔌 SDN Controller Interfaces

### ⬇️ Southbound Interfaces

Communication with network devices:

* Protocols: OpenFlow, SNMP, CLI (SSH/Telnet), P4

### ⬆️ Northbound Interfaces (APIs)

Communication with applications:

* Provide access to network resources
* Abstract device-level complexity
* Enable application-driven networking

### 🔔 Event Handling

* Controller notifies applications of network events
* Applications can:

  * Drop / modify / forward packets
  * Add / delete / update flows

---

## 🏗️ Network Control Approaches

### 1. Direct Fabric Programming

* Controller directly programs switches
* Uses protocols like OpenFlow, NETCONF
* Example controllers: OpenDaylight, ONOS, Floodlight

### 2. Overlay Networks

* Builds virtual network over existing infrastructure
* Uses encapsulation (VXLAN, GRE)
* Example: VMware NSX

| Feature                      | Direct Fabric | Overlay |
| ---------------------------- | ------------- | ------- |
| Works with existing networks | ❌             | ✅       |
| Requires encapsulation       | ❌             | ✅       |
| Scalable                     | ✅             | ✅       |

---

## 🧭 SDN and Routing

* Traditional routing = **distributed across routers**
* SDN routing = **centralized in controller**

### ✅ Benefits

* Global network view
* Optimized path computation
* Application-aware routing
* Reduced load on switches

---

## 🏛️ ITU-T SDN Model

### 📱 Application Layer

* Defines network services
* Interacts via APIs

### 🎛️ Control Layer

* **Application support** (APIs)
* **Orchestration** (resource management)
* **Abstraction** (network view)

### 🌍 Resource Layer

* Data plane devices (switches, routers)
* Handles:

  * Packet forwarding
  * Data processing

---

## 🧩 Controller Architectures

### 🏢 Centralized Controllers

* Single controller manages entire network
* Limitations:

  * Scalability
  * Single point of failure

### 🌐 Distributed Controllers

* Multiple controllers managing different domains
* Types:

  * Horizontal (split by devices)
  * Vertical (split by function)

### 📊 Benefits of Multiple Domains

* Scalability
* Reliability
* Incremental deployment
* Privacy control

---

## 🤝 Federated SDN Networks

* Multiple organizations’ SDN domains cooperate
* Share:

  * QoS policies
  * Routing info
  * Control parameters
* Communicate via **east/westbound interfaces**

---

## 🔗 Controller Communication

* **East/Westbound APIs** enable controller-to-controller communication
* Still lacks strong standardization

---

## 🛠️ SDN Controller Implementations

### Open Source

* **OpenDaylight** (Java, modular, scalable)
* **POX** (Python, simple, good for learning)
* **Floodlight** (REST API, extensible)
* **Ryu** (Python-based framework)

### Commercial / Advanced

* **Onix** (distributed controller)

### 🧪 Tools

* **Mininet**: Network emulator for testing SDN environments

---

# 🏷️ Tags

#SDN #Networking #SDNController #OpenFlow #NetworkAutomation #CloudNetworking #Virtualization #OverlayNetworks #Routing #ITU #DistributedSystems #NetworkEngineering #Mininet #OpenDaylight #Floodlight #Ryu #POX
