# Module 3 – INTRODUCTION TO NETWORKING  
## 3.14 Common Protocols – TCP, UDP, ICMP & VoIP (CDSA-Focused Notes)

Protocols are standardized communication rules defined in RFCs.  
They define:

- How data is structured  
- How devices communicate  
- How sessions are established  
- How errors are handled  

If you understand protocols, you understand network behavior.  
If you understand network behavior, you can detect abnormal behavior.

---

## 1. TCP vs UDP – The Core Difference

### TCP (Transmission Control Protocol)
- Connection-oriented  
- Uses 3-way handshake  
- Reliable  
- Ordered delivery  
- Error checking & retransmission  
- Slower due to overhead  

**TCP 3-Way Handshake**
1. SYN  
2. SYN-ACK  
3. ACK  

After this → data transfer begins.

**Used when reliability matters:**
- Web browsing (HTTP/HTTPS)  
- SSH  
- FTP  
- Email  
- SMB  
- RDP  

---

### UDP (User Datagram Protocol)
- Connectionless  
- No handshake  
- No delivery guarantee  
- Faster  
- Lower overhead  

**Used when speed matters:**
- Streaming  
- VoIP  
- DNS  
- Gaming  
- DHCP  

---

## 2. Common TCP Protocols (High-Value Targets)

| Protocol   | Port  | Security Relevance        |
|------------|-------|---------------------------|
| Telnet     | 23    | Insecure remote login     |
| SSH        | 22    | Secure remote access      |
| HTTP       | 80    | Web attacks               |
| HTTPS      | 443   | Encrypted web             |
| FTP        | 20/21 | Plaintext credentials     |
| SMB        | 445   | Lateral movement          |
| RDP        | 3389  | Brute force target        |
| LDAP       | 389   | Directory enumeration     |
| Kerberos   | 88    | Authentication abuse      |
| SMTP       | 25    | Email spoofing            |
| IMAP       | 143   | Email retrieval           |
| POP3       | 110   | Email retrieval           |
| MSSQL      | 1433  | DB exploitation           |
| Oracle TNS | 1521  | DB enumeration            |
| SIP        | 5060  | VoIP signaling            |

**High-Risk Ports in Enterprise Environments:**
- 445 (SMB)  
- 3389 (RDP)  
- 22 (SSH)  
- 389 (LDAP)  
- 88 (Kerberos)  
- 1433 (MSSQL)  

These are common pivoting points.

---

## 3. Common UDP Protocols

| Protocol | Port     | Purpose            |
|----------|----------|--------------------|
| DNS      | 53       | Name resolution    |
| DHCP     | 67/68    | IP assignment      |
| SNMP     | 161      | Device management  |
| NTP      | 123      | Time sync          |
| RIP      | 520      | Routing            |
| TFTP     | 69       | Simple file transfer |
| Syslog   | 514      | Logging            |
| NetBIOS  | 137      | Name resolution    |
| UPnP     | 1900     | Device discovery   |

UDP is often used in:
- Infrastructure services  
- Discovery mechanisms  
- Internal network control  

---

## 4. ICMP – Network Control & Diagnostics

ICMP is used for:
- Error reporting  
- Reachability testing  
- Routing feedback  

**ICMP Versions**
- ICMPv4 → IPv4  
- ICMPv6 → IPv6 (includes Neighbor Discovery)  

### Important ICMP Types

| Type                   | Purpose              |
|------------------------|----------------------|
| Echo Request           | Ping                 |
| Echo Reply             | Ping response        |
| Destination Unreachable| Delivery failure     |
| Time Exceeded          | TTL expired          |
| Redirect               | Better route         |
| Parameter Problem      | Header issue         |

---

## 5. TTL (Time-To-Live)

TTL:
- Limits packet lifetime  
- Prevents routing loops  
- Decremented at each router  

When TTL = 0 → router drops packet and sends ICMP Time Exceeded.

### TTL & OS Fingerprinting

| OS           | Default TTL |
|--------------|-------------|
| Windows      | 128         |
| Linux/macOS  | 64          |
| Solaris      | 255         |

Example:  
Ping reply TTL = 122 → Likely Windows (128 - ~6 hops)

**Note:** TTL can be manually modified.

---

## 6. VoIP & SIP (Security-Relevant)

VoIP = Voice over IP

**Common SIP Ports:**
- 5060 (unencrypted SIP)  
- 5061 (encrypted SIP)  
- 1720 (H.323 legacy)  

### SIP Methods

| Method   | Purpose            |
|----------|--------------------|
| INVITE   | Start session      |
| ACK      | Confirm            |
| BYE      | End session        |
| REGISTER | Register user      |
| OPTIONS  | Query capabilities |
| CANCEL   | Cancel session     |

**SIP Enumeration Risk**
- User enumeration  
- Service discovery  
- Capability disclosure  
- Brute-force potential  

**Cisco SEPxxxx.cnf Files**
- Reveal IP phone configuration  
- Firmware version  
- Network settings  
- Possible credentials  

Information disclosure risk.

---

## 7. Protocols Frequently Abused in Attacks

| Protocol | Common Abuse        |
|----------|--------------------|
| SMB      | Ransomware spread  |
| RDP      | Brute force        |
| LDAP     | Enumeration        |
| Kerberos | Ticket attacks     |
| DNS      | Tunneling          |
| SNMP     | Info leakage       |
| NTP      | Amplification      |
| SIP      | Enumeration        |
| FTP      | Credential theft  |
| ICMP     | Covert channels   |

---

## 8. Layer Mapping (Quick Reference)

| Layer | Examples             |
|-------|----------------------|
| L7    | HTTP, SMTP, SIP     |
| L4    | TCP, UDP            |
| L3    | IP, ICMP            |
| L2    | ARP                 |

---

## 9. What to Look for as a Defensive Analyst

When analyzing traffic:
- Unexpected TCP connections  
- UDP traffic to unknown external IPs  
- ICMP spikes  
- Repeated RDP attempts  
- DNS queries to random domains  
- SIP scanning patterns  

Protocols tell a story.  
Abnormal protocol usage often indicates compromise.

---

## 10. Interview-Level Questions

1. Difference between TCP and UDP?  
2. What is the TCP 3-way handshake?  
3. Why is UDP used for streaming?  
4. What does TTL prevent?  
5. How can TTL help OS fingerprinting?  
6. Why is SMB dangerous?  
7. What protocol does DNS use?  
8. What is SIP used for?  
