# Module 3 – INTRODUCTION TO NETWORKING  
## 3.6 The OSI Model – Layer-by-Layer Breakdown (CDSA-Focused Notes)

The OSI (Open Systems Interconnection) Model was created as a standardized reference framework to:
- Enable communication between different systems  
- Ensure interoperability across vendors and technologies  
- Visually represent how connections are established  
- Break complex networking into manageable layers  

It defines **7 hierarchical layers**, each with a specific role in communication.

---

## Why the OSI Model Exists

Before standardization:
- Vendors implemented proprietary networking systems  
- Interoperability was difficult  
- Troubleshooting lacked structure  

The OSI model provides:

> A universal language to describe networking behavior.

---

## The 7 OSI Layers (Top to Bottom)

| Layer | Name | Core Function |
|------:|------|---------------|
| 7 | Application | User-facing network services |
| 6 | Presentation | Data formatting, encryption |
| 5 | Session | Session control & management |
| 4 | Transport | End-to-end delivery control |
| 3 | Network | Routing & logical addressing |
| 2 | Data Link | Framing & MAC addressing |
| 1 | Physical | Bit transmission |

---

## Layer-by-Layer Explanation

### Layer 7 – Application
- Interface between user applications and the network  
- Handles:
  - Web browsing (HTTP/HTTPS)  
  - Email (SMTP)  
  - File transfers (FTP)  
  - DNS lookups  

**Security relevance:**
- SQL injection  
- XSS  
- API abuse  
- DNS poisoning  

---

### Layer 6 – Presentation
Responsible for:
- Data formatting  
- Encoding/decoding  
- Encryption/decryption  
- Compression  

**Examples:**
- TLS/SSL encryption  
- Data format conversion (UTF-8, ASCII)  

**Security relevance:**
- TLS inspection  
- Certificate validation issues  

---

### Layer 5 – Session
Manages:
- Session establishment  
- Session maintenance  
- Session termination  
- Checkpoints and recovery  

**Security relevance:**
- Session hijacking  
- Session fixation  

---

### Layer 4 – Transport
Provides:
- End-to-end communication  
- Reliability (TCP)  
- Speed (UDP)  
- Segmentation  
- Flow control  
- Congestion control  

**Security relevance:**
- SYN floods  
- Port scanning  
- RST injection  
- TCP session hijacking  

---

### Layer 3 – Network
Handles:
- Logical addressing (IP)  
- Routing decisions  
- Path determination  
- Packet forwarding  

**Security relevance:**
- IP spoofing  
- Routing attacks  
- BGP hijacking  
- ICMP abuse  

---

### Layer 2 – Data Link
Responsible for:
- Framing  
- MAC addressing  
- Error detection  
- Local delivery  

**Security relevance:**
- ARP spoofing  
- MAC flooding  
- VLAN hopping  

---

### Layer 1 – Physical
Handles:
- Electrical signals  
- Optical signals  
- Radio waves  
- Binary transmission  

**Security relevance:**
- Physical cable tapping  
- Signal interception  
- Hardware tampering  

---

## Layer Grouping

**Transport-Oriented Layers**
- Layer 2  
- Layer 3  
- Layer 4  

**Application-Oriented Layers**
- Layer 5  
- Layer 6  
- Layer 7  

Layer 1 supports all others physically.

---

## Communication Flow (Encapsulation)

**Sender path:**  
Layer 7 → 6 → 5 → 4 → 3 → 2 → 1  

**Receiver path:**  
Layer 1 → 2 → 3 → 4 → 5 → 6 → 7  

Each layer:
- Adds its own header (encapsulation)  
- Performs its assigned task  
- Passes data down  

On receiving:
- Each layer removes its header (decapsulation)  
- Processes relevant information  
- Passes data up  

---

## Why This Matters for Security Analysts

Every attack maps to a layer.

| Attack | OSI Layer |
|--------|-----------|
| ARP Spoofing | Layer 2 |
| IP Spoofing | Layer 3 |
| SYN Flood | Layer 4 |
| Session Hijacking | Layer 5 |
| TLS Downgrade | Layer 6 |
| SQL Injection | Layer 7 |

Understanding the OSI model allows you to:
- Pinpoint attack location  
- Design proper firewall rules  
- Interpret IDS alerts  
- Troubleshoot efficiently  
- Analyze packet captures correctly  

---

## Key Interview Concepts

1. Why does OSI have 7 layers?  
2. What layer does encryption occur?  
3. Where does TCP operate?  
4. What layer is ARP?  
5. Difference between Layer 2 and Layer 3?  
6. Why is OSI considered a reference model?
