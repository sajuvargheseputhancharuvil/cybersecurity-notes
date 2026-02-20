# Module 3 – INTRODUCTION TO NETWORKING  
## 3.8 Network Layer (OSI Layer 3) – Routing & Logical Addressing (CDSA-Focused Notes)

The Network Layer (Layer 3) is responsible for moving packets from the source network to the destination network.

Unlike Layer 2 (which works locally), Layer 3 handles communication across different networks and subnets.

> If Layer 2 delivers locally, Layer 3 delivers globally.

---

## Core Responsibilities of Layer 3

The Network Layer is responsible for:
- Logical Addressing  
- Routing  
- Path Determination  
- Packet Forwarding  
- Basic Traffic Control  

Routers operate primarily at this layer.

---

## How Layer 3 Works

When a device sends data:
1. It places the destination IP address in the packet.  
2. The packet is sent to the default gateway (router).  
3. The router checks its routing table.  
4. The router forwards the packet to the next hop.  
5. This continues node-by-node until the destination network is reached.  

**Important:**  
Routers do not process upper-layer data (e.g., HTTP content).  
They forward packets based on IP header information only.

---

## Logical Addressing

Layer 3 introduces IP addressing, which:
- Identifies networks  
- Identifies hosts within networks  
- Enables subnetting  
- Allows scalable routing  

Two main versions:
- IPv4 (32-bit)  
- IPv6 (128-bit)  

Without logical addressing:
- Inter-network communication would not be possible.

---

## Routing

Routing is the process of:
- Selecting the best path  
- Forwarding packets toward the destination  

Each router:
- Examines the destination IP  
- Looks at its routing table  
- Determines the next hop  
- Forwards the packet  

The sender does **not** need to know the full path.

---

## Packet Forwarding Between Subnets

When communication occurs between:
- Different VLANs  
- Different subnets  
- Different IP schemes  

Layer 3 enables routing between them.

**Example:**
- Host A → Subnet 1  
- Host B → Subnet 2  

Since direct Layer 2 communication isn’t possible:
- A router forwards packets between subnets.  

Forwarded packets:
- Do **not** go to higher layers on the router  
- Only the IP header is examined  
- Router assigns the next-hop destination  

---

## Key Protocols at Layer 3

### IPv4 / IPv6
Primary logical addressing protocols.

**Functions:**
- Packet structure definition  
- Addressing format  
- Fragmentation rules  

**Security risks:**
- IP spoofing  
- Fragmentation attacks  
- IPv6 misconfiguration exploitation  

---

### IPsec
Provides:
- Encryption  
- Authentication  
- Integrity protection  

**Used in:**
- VPN tunnels  
- Secure site-to-site communication  

**Security importance:**
- Protects data at Layer 3  
- Prevents packet tampering  

---

### ICMP
Used for:
- Error messages  
- Network diagnostics  

**Examples:**
- Ping  
- Traceroute  

**Security risks:**
- ICMP tunneling  
- Network mapping  
- Smurf attacks  

---

### IGMP
Used for:
- Multicast group management  
- Streaming communication control  

Common in:
- IPTV  
- Multicast routing  

---

### RIP (Routing Information Protocol)
Distance-vector routing protocol:
- Simple  
- Older  
- Limited scalability  

**Security risks:**
- Route poisoning  
- Malicious route injection  

---

### OSPF (Open Shortest Path First)
Link-state routing protocol:
- Faster convergence  
- More scalable  
- Common in enterprise networks  

**Security risks:**
- Malicious LSAs  
- Route manipulation if not authenticated  

---

## Summary of Layer 3 Functions

| Function              | Description                         |
|-----------------------|-------------------------------------|
| Logical Addressing    | IP address assignment               |
| Routing               | Determining best path               |
| Packet Forwarding     | Moving packets hop-by-hop           |
| Subnet Communication  | Inter-network communication         |
| Flow Control          | Basic congestion handling           |

---

## Defensive Security Perspective (CDSA Focus)

Layer 3 is critical because:
- It defines trust boundaries between subnets  
- It enables segmentation  
- It controls inter-VLAN routing  
- It determines external exposure  

**Common attack categories:**

| Attack                 | Layer 3 Involvement              |
|------------------------|----------------------------------|
| IP Spoofing            | Source IP manipulation           |
| Routing Table Poisoning| Malicious route injection        |
| ICMP Abuse             | Reconnaissance                   |
| BGP Hijacking          | WAN routing attack               |
| Lateral Movement       | Poor subnet segmentation         |

---

## Practical Example

If:
- Printer network talks to server network  
- IoT devices talk to domain controller  
- Guest Wi-Fi reaches internal subnet  

That is a **Layer 3 design failure**.

**Proper Layer 3 segmentation includes:**
- VLAN separation  
- ACLs on routers  
- Inter-subnet firewall rules  
- Zero-trust routing design  

---

## Interview-Level Questions

1. What is the primary responsibility of Layer 3?  
2. How does routing differ from switching?  
3. What is the difference between IPv4 and IPv6?  
4. What protocol does ping use?  
5. What happens inside a router when forwarding a packet?  
6. Why is Layer 3 segmentation important for security?
