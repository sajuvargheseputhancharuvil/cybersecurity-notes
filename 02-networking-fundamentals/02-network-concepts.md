# Network Concepts

This section builds the technical backbone of networking.  
If “Introduction to Networks” explained *what* networks are, this section explains *how* they function under the hood.

**Why this matters for defenders:**
- Every attack maps to a layer  
- Every detection strategy depends on understanding data flow  
- Most incident analysis uses layered troubleshooting logic  

---

## OSI Model (7 Layers – Conceptual Framework)

The OSI model is a theoretical framework used to understand how data flows through a network in structured layers.

It is not directly implemented, but it is extremely important for:
- Troubleshooting  
- Threat analysis  
- Explaining attacks during interviews  

---

## OSI Layers (Bottom → Top)

### Layer 1 – Physical
- Transmits raw bits (0s and 1s)  
- Hardware: cables, NICs, voltage signals  

**Examples:**  
- Ethernet cables  
- Hubs  
- Repeaters  

**Security view:**  
Physical access = total compromise. Cable tapping and hardware tampering occur here.

---

### Layer 2 – Data Link
- Node-to-node communication  
- MAC addressing  
- Framing and error detection (CRC)  

**Devices:** Switches, bridges  

**Common attacks:**  
- ARP spoofing  
- MAC flooding  
- VLAN hopping  

> Heavily targeted in internal LAN attacks.

---

### Layer 3 – Network
- Logical addressing (IP)  
- Routing between networks  
- Path determination  

**Device:** Router  
**Protocol:** IP  

**Common attacks:**  
- IP spoofing  
- Route injection  
- ICMP abuse  
- Network scanning  

> Most reconnaissance operates at Layer 3.

---

### Layer 4 – Transport
- End-to-end communication  
- Segmentation and reassembly  
- Reliability and flow control  

**Protocols:**  
- TCP – Reliable, connection-oriented  
- UDP – Fast, connectionless  

**Security impact:**  
- Port scanning  
- SYN flood attacks  
- Session hijacking  

> Understanding the TCP handshake is critical for CDSA.

---

### Layer 5 – Session
- Manages sessions between systems  
- Session establishment and termination  
- Checkpointing  

**Threats:**  
- Session hijacking  
- Token reuse  
- Authentication bypass  

---

### Layer 6 – Presentation
- Data formatting  
- Encryption and decryption  
- Compression  

**Security note:**  
TLS encryption is conceptually placed here.  
If encryption fails, data is exposed.

---

### Layer 7 – Application
- User-facing network services  
- Interfaces with applications  

**Examples:**  
- HTTP  
- FTP  
- SMTP  
- DNS  

**Most targeted layer:**  
- SQL injection  
- XSS  
- File upload abuse  
- Phishing  

---

## Encapsulation (Sending a File)

Data flows downward through layers before transmission:

1. Application initiates request  
2. Presentation encrypts  
3. Session establishes connection  
4. Transport segments data  
5. Network assigns IP routing  
6. Data Link frames it  
7. Physical transmits bits  

On the receiving end, the process reverses (**decapsulation**).

> **Interview keyword:** Encapsulation

---

## TCP/IP Model (Practical Internet Model)

Unlike OSI, TCP/IP is actually implemented.  
It simplifies OSI’s 7 layers into 4.

### TCP/IP vs OSI Mapping

| TCP/IP Layer   | OSI Layers Equivalent                 |
|----------------|----------------------------------------|
| Link           | Physical + Data Link                   |
| Internet       | Network                                |
| Transport      | Transport                              |
| Application    | Session + Presentation + Application   |

---

### TCP/IP Layers

**Link Layer**
- Hardware addressing  
- Ethernet, Wi-Fi  
- Physical transmission  

**Internet Layer**
- Logical addressing  
- Routing  
- IP, ICMP  

**Transport Layer**
- TCP (reliable)  
- UDP (fast, unreliable)  
- Ports, connections, flow control  

**Application Layer**
- HTTP  
- FTP  
- SMTP  
- DNS  

---

### Example: Accessing a Website

1. Browser sends HTTP request (Application)  
2. TCP establishes connection (Transport)  
3. IP routes packets (Internet)  
4. Ethernet/Wi-Fi transmits data (Link)  

---

## OSI vs TCP/IP (Interview Clarity)

| Feature  | OSI                    | TCP/IP                   |
|----------|------------------------|--------------------------|
| Layers   | 7                      | 4                        |
| Purpose  | Theoretical model      | Practical implementation|
| Used for | Learning, troubleshooting | Real-world networking |

> **Strong interview answer:**  
> OSI helps identify where a problem occurs. TCP/IP is what actually runs the internet.

---

## Network Protocols (Rules of Communication)

Protocols define how data is structured and exchanged. Each operates at specific layers.

### Key Protocols for CDSA

**HTTP**
- Transfers web content  
- Application layer  
- Stateless  
- Risk: MITM if not encrypted  

**FTP**
- File transfer  
- Application layer  
- Separate control and data channels  
- Risk: Cleartext credentials  

**SMTP**
- Email transmission  
- Application layer  
- Risk: Email spoofing, phishing  

**TCP**
- Reliable delivery  
- 3-way handshake  
- Targeted by SYN floods, session hijacking  

**UDP**
- Fast, connectionless  
- Used by DNS, streaming  
- Risk: Amplification attacks  

**IP**
- Logical addressing  
- Packet routing  
- Enables scanning and spoofing  

---

## Transmission Concepts

Understanding transmission helps with:
- Network forensics  
- Performance troubleshooting  
- Detection engineering  

### Transmission Types
- **Analog:** Continuous signals (radio)  
- **Digital:** Binary (0s and 1s) – used in networks  

### Transmission Modes

| Mode        | Description                 | Example              |
|-------------|-----------------------------|----------------------|
| Simplex     | One-way                     | Keyboard → Computer  |
| Half-duplex | Two-way, not simultaneous   | Walkie-talkie        |
| Full-duplex | Two-way, simultaneous       | Phone call           |

> Most modern Ethernet is full-duplex.

---

### Transmission Media

**Wired**
- Twisted pair (Ethernet)  
- Coaxial cable  
- Fiber optic (backbone, high speed)  

> Fiber is harder to tap, but not impossible.

**Wireless**
- Radio (Wi-Fi, cellular)  
- Microwave (satellite)  
- Infrared (short range)  

**Wireless risks:**
- Sniffing  
- Evil twin attacks  
- Signal interception  

---

## Defensive Analyst Takeaways (CDSA)

- Every attack maps to a network layer  
- Troubleshooting follows layer-based logic  
- TCP/IP is operational; OSI is conceptual  
- TCP vs UDP behavior affects detection strategy  
- Most exploitation happens at Layer 7  
- Lateral movement often abuses Layers 2–4  

---

## High-Value Interview Questions

Be ready to answer:
1. Explain OSI vs TCP/IP differences  
2. What layer does a router operate at?  
3. Why is TCP more reliable than UDP?  
4. What is encapsulation?  
5. Which layer is most targeted in cyber attacks?  
6. How does data move when accessing a website?  
