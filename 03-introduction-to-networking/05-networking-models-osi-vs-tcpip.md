# Module 3 – INTRODUCTION TO NETWORKING  
## 3.5 Networking Models – OSI vs TCP/IP (CDSA-Focused Notes)

Two primary models describe how data moves from one host to another:
- OSI Model (ISO/OSI)  
- TCP/IP Model  

These are conceptual frameworks, not physical systems.  
They help us understand how raw bits become usable application data.

---

## 1. OSI vs TCP/IP – High-Level Comparison

| OSI Model (7 Layers) | TCP/IP Model (4 Layers) |
|----------------------|-------------------------|
| Application          | Application             |
| Presentation         |                         |
| Session              |                         |
| Transport            | Transport               |
| Network              | Internet                |
| Data Link            | Link                    |
| Physical             | Link                    |

---

## 2. The OSI Model (ISO/OSI)

OSI stands for **Open Systems Interconnection**.

Published by:
- ISO (International Organization for Standardization)  
- ITU (International Telecommunication Union)  

It is a reference model used to describe communication between systems.

### OSI 7 Layers Overview

| Layer | Purpose |
|------|---------|
| 7 – Application | Interface for applications (HTTP, FTP, SMTP) |
| 6 – Presentation | Encryption, compression, formatting |
| 5 – Session | Session management |
| 4 – Transport | Reliable delivery (TCP/UDP) |
| 3 – Network | Logical addressing (IP, routing) |
| 2 – Data Link | MAC addressing, framing |
| 1 – Physical | Bit transmission over media |

### Why OSI Matters for Security

OSI helps analysts:
- Break down attacks layer by layer  
- Identify where an issue occurs  
- Analyze traffic systematically  
- Troubleshoot efficiently  

**Examples:**
- ARP spoofing → Layer 2  
- DNS poisoning → Layer 7  
- SYN flood → Layer 4  

---

## 3. The TCP/IP Model

TCP/IP is the practical implementation model used on the Internet.

> **Important:** TCP/IP is not just TCP and IP.

It includes protocols such as:
- TCP  
- IP  
- UDP  
- ICMP  
- ARP  
- DNS (Application-layer protocols)  

The entire Internet operates on this protocol family.

### TCP/IP 4 Layers

| Layer | Function |
|-------|----------|
| Application | HTTP, FTP, DNS, SMTP |
| Transport | TCP, UDP |
| Internet | IP, ICMP |
| Link | Ethernet, MAC, Physical transmission |

### Practical View

TCP/IP is:
- Implementation-focused  
- Less strict than OSI  
- Real-world standard  

OSI is:
- Analytical framework  
- Conceptual model  
- Used heavily for troubleshooting and exams  

---

## 4. OSI vs TCP/IP – Key Differences

| Feature | OSI | TCP/IP |
|--------|-----|--------|
| Layers | 7 | 4 |
| Usage | Theoretical / Analytical | Practical / Operational |
| Strict separation | Yes | More flexible |
| Used on Internet | No | Yes |

---

## 5. Packet Transfer & PDUs

In layered communication, each layer uses a **Protocol Data Unit (PDU)**.

| Layer | PDU Name |
|-------|----------|
| Application | Data |
| Transport | Segment (TCP) / Datagram (UDP) |
| Network | Packet |
| Data Link | Frame |
| Physical | Bits |

---

## 6. Encapsulation Process

When sending data:
1. Application creates data  
2. Transport layer adds TCP/UDP header → Segment  
3. Network layer adds IP header → Packet  
4. Data Link layer adds MAC header → Frame  
5. Physical layer converts to bits  

This process is called:

> **Encapsulation**

### Decapsulation

On the receiving side:
- Each layer removes its header  
- Data moves upward  
- Application finally receives usable data  

---

## 7. Example – Website Access Flow (Layered View)

When browsing a website:
1. Browser generates HTTP request (Application)  
2. TCP wraps request with ports (Transport)  
3. IP wraps with source/destination IP (Network)  
4. Ethernet frame wraps with MAC (Data Link)  
5. Bits transmitted over medium (Physical)  

At the server, the reverse process occurs.

---

## 8. Defensive Security Importance (CDSA Focus)

Understanding networking models helps in:
- Traffic analysis  
- Packet inspection  
- Incident response  
- Malware communication analysis  
- Firewall rule design  
- IDS alert interpretation  

**Examples:**
- IDS alerts on TCP flags → Layer 4 issue  
- Malicious HTTP payload → Layer 7 issue  
- Suspicious ARP → Layer 2 issue  

---

## 9. Penetration Testing Perspective

TCP/IP:
- Helps understand full connection lifecycle  

OSI:
- Helps isolate attack layer precisely  

When analyzing captured traffic:
- You mentally map packets to OSI layers  

---

## 10. Interview Questions You Should Handle

1. Difference between OSI and TCP/IP?  
2. Why does TCP/IP have fewer layers?  
3. What is encapsulation?  
4. What PDU exists at Layer 3?  
5. Which layer handles encryption?  
6. Where does ARP operate?  
7. Why is OSI useful in troubleshooting?
