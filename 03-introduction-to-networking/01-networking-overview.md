## 3.1 Networking Overview

**Networking is not just connectivity — it is control.**

As security professionals, misunderstanding networking can lead to:
- Silent failures  
- Missed detections  
- Incorrect assumptions  
- Poor segmentation  

And sometimes, completely missing high-value targets.

---

## 1. Networks Are Not Just “Connected Devices”

A network consists of:
- Topologies (Star, Mesh, Tree)  
- Mediums (Ethernet, Fiber, Wireless)  
- Protocols (TCP, UDP, etc.)

A flat network might work operationally.  

But:

> **Operational ≠ Secure**

---

## 2. Flat Network vs Segmented Network

A flat network (e.g., single `/24` subnet) allows:
- All devices to talk freely  
- Minimal isolation  
- Easy lateral movement  

**Security analogy:**  
A house with one lock on the front door.

### Why Segmentation Matters

Breaking large networks into smaller subnets:
- Slows attackers  
- Limits lateral movement  
- Enables monitoring per segment  
- Improves logging clarity  

### Example – Security Layers Analogy

| Network Control | House Analogy |
|-----------------|---------------|
| ACLs            | Fence with controlled gates |
| Documentation  | Lights around house |
| IDS/IPS         | Alarm system |
| Segmentation    | Separate locked rooms |

If the printer network talks to the internet → suspicious.  
If a printer scans servers via HTTP → suspicious.  

**Segmentation makes anomalies visible.**

---

## 3. Subnetting Mistakes – Real Pentest Example

Most people default to:

/24 → 255.255.255.0
192.168.1.1 – 192.168.1.254

All devices communicate freely.

### /25 Example

10.20.0.0   – 10.20.0.127
10.20.0.128 – 10.20.0.255

Devices in one half cannot communicate directly with the other without routing.

### Pentester Oversight

Pentester used:

10.20.0.252/24

Actual network:

10.20.0.1/25    (Server Network)
10.20.0.129/25  (Client Network)

**Result:**
- Could access workstations  
- Could not reach Domain Controller  
- Incorrectly assumed DC was offline  

**Lesson:**  
Always verify subnet mask and routing.

For CDSA:
- Lateral movement detection  
- Network discovery  
- Firewall rule analysis  

all depend on subnet boundaries.

---

## 4. Home vs Company Network Architecture

High-level view:

Home Network → ISP → Company Network

Communication resembles mail delivery:
- URL = Address  
- DNS = Phonebook  
- Router = Local Post Office  
- ISP = Main Distribution Center  

---

## 5. URL vs FQDN (Important Distinction)

| Term | Meaning |
|------|--------|
| FQDN | www.example.com |
| URL  | https://www.example.com/path?query |

FQDN = Address of building  
URL = Specific room, floor, mailbox  

**Security relevance:**
- URL filtering works at deeper level  
- Domain blocking works at FQDN level  

---

## 6. Proper Enterprise Segmentation (Critical for CDSA)

A secure enterprise design includes multiple segmented networks.

### 1. Web Server → DMZ

- Internet-facing  
- Higher risk of compromise  
- Isolated from internal LAN  

DMZ allows:

Internet → Web Server
Web Server ✖ Internal Network

### 2. Workstations → Separate Network

- Prevent workstation-to-workstation attacks  
- Reduce ARP spoofing risk  
- Limit lateral movement  

Ideally:
- Host-based firewall blocks lateral traffic.

### 3. Administration Network

- Switches and routers isolated  
- Prevent routing protocol abuse  
- Protect against OSPF manipulation  

Real-world risk:
- Unprotected routing protocols allow route injection.

### 4. Voice (IP Phones) Network

- QoS requirements  
- Prevent eavesdropping  
- Separate broadcast domain  

### 5. Printer Network (Often Overlooked)

Printers:
- Hard to secure  
- Store sensitive documents  
- Trigger NTLM authentication  
- Often poorly patched  

**Real threat:**  
Printer forces NTLMv2 authentication → Credential capture.

---

## 7. Real-World Attack Story (Key Lessons)

**Attack Summary:**
- Attacker purchased printer  
- Embedded reverse shell  
- Shipped printer to company  
- Phishing email sent  
- Printer connected internally  
- Domain Admin credentials captured  

### Why It Worked

- Printer had internet access  
- SMB allowed to workstations (port 445)  
- Printer initiated outbound connections  
- No segmentation  

### Why It Should Have Failed

With proper segmentation:
- Printer network isolated  
- No outbound internet access  
- No SMB to workstations  
- Strict ACLs  

**Defense in depth would have stopped it.**

---

## 8. Critical Defensive Takeaways

- Flat networks enable lateral movement  
- Subnet masks matter  
- Segmentation slows attackers  
- DMZ isolates internet-facing systems  
- Printers are high-risk devices  
- Administrative networks must be protected  
- Routing protocols must be secured  

---

## 9. Attack Surface by Device Type

| Device       | Risk |
|-------------|------|
| Web Server  | External exploitation |
| Workstation | Phishing & malware |
| Router      | Route manipulation |
| Switch      | ARP spoofing |
| Printer     | Credential harvesting |
| IP Phone    | VoIP sniffing |

---

## 10. Interview-Level Questions

1. What is a flat network?  
2. Why is segmentation important?  
3. What is a DMZ?  
4. Why isolate printers?  
5. What is the risk of misconfigured OSPF?  
6. What can happen if subnet mask is wrong?
