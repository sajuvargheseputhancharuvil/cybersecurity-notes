# Module 3 – INTRODUCTION TO NETWORKING  
## 3.3 Networking Topologies – Physical vs Logical Design (CDSA-Focused Notes)

A network topology describes how devices are arranged and interconnected in a network.

It determines:
- How devices communicate  
- What hardware is required  
- How resilient the network is  
- How easy it is to secure  

Understanding topology is critical in defensive security because:

> Topology directly impacts attack surface, segmentation, and monitoring visibility.

---

## 1. Physical vs Logical Topology

### Physical Topology
Describes:
- Physical cabling layout  
- Device placement  
- Hardware connections  

Example:  
How switches and cables are physically connected.

---

### Logical Topology
Describes:
- How data flows  
- How signals move  
- How communication occurs  

Example:  
Token-based ring running on physically star-connected devices.

> **Important:** Physical layout ≠ Logical data flow.

---

## 2. Three Core Areas of Topology

### 1. Connections (Transmission Media)

**Wired**
- Twisted Pair (Ethernet)  
- Coaxial  
- Fiber Optic  

**Wireless**
- Wi-Fi  
- Cellular  
- Satellite  

---

### 2. Nodes (Network Devices)
- NICs  
- Repeaters  
- Hubs  
- Switches  
- Routers  
- Gateways  
- Firewalls  

Nodes are connection points that transmit or receive signals.

---

### 3. Classification (Topology Type)

There are 8 fundamental topologies:
- Point-to-Point  
- Bus  
- Star  
- Ring  
- Mesh  
- Tree  
- Hybrid  
- Daisy Chain  

Complex networks are often combinations of these.

---

## 3. Point-to-Point Topology

Simplest topology.  
Two devices connected directly.

Used in:
- Direct WAN links  
- Traditional telephony  

**Security impact:**
- Minimal attack surface  
- No segmentation complexity  

> Do not confuse with Peer-to-Peer architecture.

---

## 4. Bus Topology

All devices share a single communication medium.

**Characteristics:**
- No central controller  
- Shared bandwidth  
- Only one device transmits at a time  

**Security issues:**
- Easy packet sniffing  
- Broadcast-based  
- Collision risk  

Rare in modern enterprise networks.

---

## 5. Star Topology

Most common modern topology.

All devices connect to a central device (switch/router).

**Advantages:**
- Easy management  
- Easy fault isolation  
- Scalable  

**Disadvantages:**
- Central device is a single point of failure  

**Security perspective:**
- Easier to monitor centrally  
- Supports VLAN segmentation  

Most LANs use star topology.

---

## 6. Ring Topology

Each device connects to two others, forming a loop.

**Characteristics:**
- Data travels in one direction  
- Often uses token passing  
- No central device required  

Logical ring can run over physical star.

**Security:**
- Predictable flow  
- Failure of one node can impact entire ring (unless redundant)  

Rare in modern networks (legacy Token Ring).

---

## 7. Mesh Topology

Nodes interconnect with multiple paths.

**Types:**
- Fully Meshed  
- Partially Meshed  

**Fully Meshed:**
- Every node connects to every other node  
- High redundancy  
- High reliability  

**Partially Meshed:**
- Some nodes interconnected  
- Balanced cost vs redundancy  

Used in:
- WAN environments  
- High-availability infrastructure  

**Security advantage:**
- Fault tolerance  
- Harder to disrupt network entirely  

---

## 8. Tree Topology

Extended star topology with hierarchy.

Common in:
- Enterprise networks  
- Structured cabling systems  

**Hierarchy:**
- Core → Distribution → Access  

**Security:**
- Enables segmentation  
- Clear policy boundaries  
- Supports VLAN architecture  

---

## 9. Hybrid Topology

Combination of two or more topologies.

Example:  
Tree + Star combination.

Most real-world enterprise networks are hybrid.

**Security impact:**
- Complexity increases  
- Requires proper documentation  
- Misconfiguration risk is higher  

---

## 10. Daisy Chain Topology

Devices connected sequentially.

Used in:
- Industrial automation (CAN)  
- Hardware chaining  

**Security concerns:**
- Single failure breaks downstream devices  
- Harder to isolate issues  

---

## 11. Topology & Security Correlation (CDSA Insight)

| Topology    | Security Consideration        |
|-------------|-------------------------------|
| Bus         | Easy sniffing                 |
| Star        | Central monitoring point      |
| Ring        | Predictable flow              |
| Mesh        | Resilient to disruption       |
| Tree        | Supports segmentation         |
| Daisy Chain | Single point chain failure    |

---

## 12. Real-World Observation

Modern enterprise networks are typically:

> Hybrid + Tree + Star  
> With mesh WAN connectivity.

Very rarely:
- Pure bus  
- Pure ring  

---

## 13. Interview-Level Questions

1. Difference between physical and logical topology?  
2. Most common topology in LAN?  
3. Which topology provides highest redundancy?  
4. Why is bus topology insecure?  
5. What topology do enterprises commonly use?  
