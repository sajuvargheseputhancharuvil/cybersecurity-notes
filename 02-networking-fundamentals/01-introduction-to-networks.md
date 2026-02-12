# Introduction to Networks

## What Is a Network?

A **network** is a group of interconnected devices that can communicate and share data or resources.

**Core components:**
- **Nodes** – End devices (PCs, servers, smartphones, printers)  
- **Links** – Communication paths (wired like Ethernet, or wireless like Wi-Fi)  
- **Data Sharing** – Exchanging information between devices  

> **Security insight (CDSA perspective):**  
> Every node increases the attack surface. More connected devices = more potential entry points for attackers.

---

## Why Networks Matter (Security Perspective)

Networks enable:
- Resource sharing (printers, storage, applications)  
- Communication (email, VoIP, messaging, video conferencing)  
- Centralized data access  
- Remote collaboration  

From a defensive analyst’s perspective:
- Data in motion must be protected  
- Shared resources must be controlled  
- Communication channels can be abused (phishing, C2 traffic, data exfiltration)  

> Modern cybersecurity exists because everything is interconnected.

---

## Types of Networks

The core types covered here:
- **LAN (Local Area Network)**  
- **WAN (Wide Area Network)**  

Understanding the difference is critical for:
- Network segmentation  
- Traffic monitoring  
- Perimeter defense  
- Incident response  

---

## Local Area Network (LAN)

### Definition
A **LAN** connects devices within a limited geographical area (home, office, school).

### Key Characteristics
- Small coverage area  
- Usually privately owned  
- High speed (low latency)  
- Uses Ethernet or Wi-Fi  

### Example
**Home network:**
- Router connects devices  
- Devices share files and internet access  

### Security Relevance
- Internal lateral movement happens inside LANs  
- Poor segmentation allows attackers to pivot easily  
- Misconfigured Wi-Fi enables internal compromise  
- ARP spoofing and internal sniffing attacks occur in LAN environments  

> **Interview tip:**  
> Most breaches escalate because once attackers enter the LAN, internal trust assumptions allow rapid movement.

---

## Wide Area Network (WAN)

### Definition
A **WAN** connects multiple LANs over large geographical areas.

### Key Characteristics
- Covers cities, countries, continents  
- Managed by ISPs or telecom providers  
- Higher latency than LAN  
- Uses fiber optics, leased lines, satellite links  

### Largest Example
The **Internet** (a global WAN connecting millions of LANs).

### Security Relevance
- Public exposure increases risk  
- Traffic interception is possible without encryption  
- DDoS attacks target WAN-facing infrastructure  
- VPNs secure WAN communications  

> **Defensive note:**  
> WAN connections must always assume a hostile environment.

---

## LAN vs WAN (Comparison)

| Aspect          | LAN                 | WAN                     |
|-----------------|---------------------|-------------------------|
| Size            | Small / local       | Large / global          |
| Ownership       | Single entity       | Multiple providers      |
| Speed           | High                | Lower (distance-based)  |
| Cost            | Lower               | Higher                  |
| Security focus  | Internal threats    | External threats        |

**For CDSA preparation:**
- LAN → internal monitoring & segmentation  
- WAN → perimeter defense, encryption, secure tunneling  

---

## How LANs and WANs Work Together

A LAN connects to a WAN through networking devices.

### Home Example (Traffic Flow)

> Device → Router → Modem → ISP → Internet


**Key components:**
- **Router** – Manages internal traffic and routes external traffic  
- **Modem** – Converts signals for ISP transmission  
- **ISP** – Provides internet connectivity  

### Business Example
- Multiple office LANs  
- Connected through a corporate WAN  
- Centralized services (databases, email servers)  

### Security Implications
- Edge devices (routers/firewalls) are critical control points  
- Misconfigured router/modem exposes the internal network  
- Remote office WAN links must be encrypted (VPN/IPsec)  

---

## Interview-Level Summary

**Q: Explain networks in simple terms.**  
A network is a system of interconnected devices that communicate and share resources. In cybersecurity, understanding how LANs and WANs interact is essential because threats can originate internally within a LAN or externally through WAN connections.

**Q: Why is networking important for a defensive analyst?**  
Because monitoring, detecting, and responding to threats depends on understanding how data flows between nodes across LANs and WANs.

---

## Key Takeaways for CDSA Preparation

- Every connected device is a potential attack surface  
- LAN security focuses on internal segmentation and monitoring  
- WAN security focuses on encryption and perimeter defense  
- Routers and modems are critical security boundaries  
- The Internet is a large-scale WAN interconnecting LANs  
