# Module 3 – INTRODUCTION TO NETWORKING  
## 3.7 The TCP/IP Model – Practical Internet Model (CDSA-Focused Notes)

The TCP/IP model, also known as the Internet Protocol Suite, is the practical networking model used on the Internet.

The name comes from two core protocols:
- **Transmission Control Protocol (TCP)** → Reliable transport  
- **Internet Protocol (IP)** → Logical addressing & routing  

**Mapping to OSI:**
- IP ≈ OSI Layer 3 (Network)  
- TCP ≈ OSI Layer 4 (Transport)  

---

## TCP/IP 4-Layer Structure

| TCP/IP Layer | Function |
|--------------|----------|
| 4. Application | Application protocols & services |
| 3. Transport | End-to-end communication (TCP/UDP) |
| 2. Internet | Logical addressing & routing (IP) |
| 1. Link | Physical transmission & framing |

---

## Layer-by-Layer Breakdown

### 1) Link Layer

**Equivalent to:**
- OSI Layer 1 (Physical)  
- OSI Layer 2 (Data Link)  

**Responsible for:**
- Frame transmission  
- MAC addressing  
- Media access  
- Physical signaling  

**Important:**
TCP/IP is designed to work independently of:
- Network medium  
- Frame format  
- Hardware type  

**Security relevance:**
- ARP spoofing  
- MAC flooding  
- VLAN hopping  
- NIC-based attacks  

---

### 2) Internet Layer

**Core protocol:** IP  

**Responsible for:**
- Logical addressing  
- Packet forwarding  
- Routing decisions  
- Fragmentation  

**Key protocols:**
- IP (IPv4 / IPv6)  
- ICMP  
- ARP (often associated conceptually)  

**Security relevance:**
- IP spoofing  
- ICMP abuse  
- Routing manipulation  
- Subnet misconfiguration  

---

### 3) Transport Layer

Provides two main services:

**TCP (Connection-Oriented)**
- Reliable delivery  
- Three-way handshake  
- Congestion control  
- Error detection  
- Flow control  

**UDP (Connectionless)**
- Fast  
- No guarantee of delivery  
- Used for streaming, VoIP, DNS  

**Security relevance:**
- SYN floods  
- RST injection  
- Port scanning  
- Session hijacking  

---

### 4) Application Layer

Contains application protocols such as:
- HTTP / HTTPS  
- FTP  
- SMTP  
- DNS  
- SSH  

This layer defines:
- How applications communicate  
- Data format expectations  
- Request/response structures  

**Security relevance:**
- SQL Injection  
- XSS  
- Command Injection  
- API abuse  
- DNS poisoning  

---

## OSI vs TCP/IP – Key Differences

| Feature | OSI | TCP/IP |
|--------|-----|--------|
| Layers | 7 | 4 |
| Nature | Theoretical framework | Practical implementation |
| Separation | Strict | Combined responsibilities |
| Usage | Reference model | Operational model |

**Layer merging in TCP/IP:**
- OSI Application + Presentation + Session → TCP/IP Application  
- OSI Data Link + Physical → TCP/IP Link  

---

## Core Responsibilities of TCP/IP

### 1) Logical Addressing – IP

**Problem:**  
Many hosts across different networks need unique addressing.

**Solution:**  
IP provides logical structure via:
- Subnetting  
- CIDR notation  

**Ensures:**  
Packets reach the correct network.

---

### 2) Routing – IP

Each router:
- Examines destination IP  
- Determines next hop  
- Forwards packet  

Sender does **not** need to know the full path.

**Security impact:**
- Route hijacking  
- BGP attacks  
- Incorrect static routes  

---

### 3) Error & Control Flow – TCP

TCP establishes a virtual connection between sender and receiver.

Maintains:
- Sequence numbers  
- Acknowledgments  
- Window sizes  
- Retransmissions  

**Ensures:**
- Data arrives correctly  
- Connection stability  

---

### 4) Application Support – Ports

TCP & UDP use ports.

Ports allow:
- Multiple applications on the same IP  
- Traffic separation  

**Examples:**
- HTTP → 80  
- HTTPS → 443  
- DNS → 53  

**Security perspective:**
- Port scanning identifies exposed services  
- Firewall rules are often port-based  

---

### 5) Name Resolution – DNS

Humans use names.  
Machines use IP addresses.

DNS translates:

`FQDN → IP address`  

**Example:**  
`www.example.com → 93.184.216.34`

**Security risks:**
- DNS spoofing  
- Cache poisoning  
- DNS tunneling  

---

## Why TCP/IP Matters More in Practice

The Internet runs entirely on TCP/IP.

As defenders, you must understand:
- How connections are established  
- How routing decisions are made  
- How transport reliability works  
- How DNS resolution fits into traffic flow  
- How ports expose services  

---

## Defensive Security Mapping

| Attack | TCP/IP Layer |
|--------|--------------|
| ARP Spoofing | Link |
| IP Spoofing | Internet |
| SYN Flood | Transport |
| SQL Injection | Application |
| DNS Tunneling | Application |

---

## Interview-Level Questions

1. Why is TCP/IP more practical than OSI?  
2. What does IP guarantee?  
3. What does TCP guarantee?  
4. Where does DNS operate?  
5. Difference between TCP and UDP?  
6. Why is TCP connection-oriented?  
7. What is CIDR?  

---

## CDSA Takeaway

Think of TCP/IP as:

> The operational blueprint of the Internet.

Use **OSI** for:
- Structured troubleshooting  

Use **TCP/IP** for:
- Real-world traffic analysis  
- Incident response  
- Packet-level investigation  
