# Module 3 – INTRODUCTION TO NETWORKING  
## 3.20 TCP/UDP Connections & IP Packet Internals (CDSA-Focused Notes)

This section moves from protocol theory into packet-level behavior — critical for:
- Packet analysis (Wireshark / tcpdump)
- Threat detection
- IDS/IPS tuning
- Network forensics
- Lateral movement analysis

---

## 1. TCP vs UDP – Beyond the Basics

You already know:
- TCP = reliable  
- UDP = fast  

From a defender’s perspective, the difference is about **state, visibility, and abuse potential**.

---

### TCP (Connection-Oriented)

TCP ensures:
- Reliability  
- Ordered delivery  
- Error recovery  
- Flow control  
- Congestion control  

**TCP 3-Way Handshake**
1. SYN  
2. SYN-ACK  
3. ACK  

After this, the connection is established.

This handshake is critical for:
- Firewall state tracking  
- IDS/IPS detection  
- SYN flood detection  
- Session correlation  

---

### TCP Flags (Critical for Analysis)

| Flag | Meaning            |
|------|--------------------|
| SYN  | Start connection   |
| ACK  | Acknowledge        |
| FIN  | Graceful close     |
| RST  | Force reset        |
| PSH  | Push data          |
| URG  | Urgent data        |

Examples:
- SYN flood → many SYNs without ACK  
- RST injection → forced connection termination  

---

### TCP Reliability Mechanisms

TCP uses:
- Sequence numbers  
- Acknowledgments  
- Window size  
- Retransmissions  

If packets are missing, TCP requests retransmission.  
This reliability is why TCP is slower but dependable.

---

## 2. UDP (Connectionless)

UDP provides:
- No handshake  
- No retransmission  
- No flow control  
- No congestion control  

Common use cases:
- DNS  
- VoIP  
- Streaming  
- Gaming  
- NTP  

**Security perspective:**  
UDP is easier to spoof because there is no session state.

---

## 3. IP Packet Structure

An IP packet contains:
1. Header  
2. Payload (TCP/UDP data)

Analogy:
- IP = envelope  
- TCP/UDP = letter inside  

---

## 4. IP Header Fields (Security-Relevant)

| Field            | Why It Matters                  |
|------------------|----------------------------------|
| Version          | IPv4 vs IPv6                     |
| IHL              | Header length                    |
| Total Length     | Anomaly detection                |
| Identification   | Fragmentation tracking           |
| Flags            | DF / MF bits                     |
| Fragment Offset  | Reassembly                       |
| TTL              | Hop count                        |
| Protocol         | TCP / UDP / ICMP                 |
| Checksum         | Header integrity                 |
| Source/Dest IP   | Core routing and attribution     |

---

## 5. IP Identification (IP ID) Field

16-bit value used for fragmentation tracking.

Security use case:

If you observe sequential IP IDs across different source IPs:
- Likely the same host  
- Useful for NAT detection  
- Multi-homed host detection  
- Correlation analysis  
- OS fingerprinting  

---

## 6. Fragmentation & Evasion

Fragmentation can be abused to:
- Split malicious payloads  
- Bypass IDS/IPS  
- Use overlapping fragments  
- Perform tiny fragment attacks  

Defensive requirement:
- Firewalls and IDS should reassemble and normalize packets.

---

## 7. TTL (Time-To-Live)

TTL:
- Decremented by each router  
- Prevents infinite routing loops  

Security uses:
- OS fingerprinting  
- Hop-distance estimation  
- TTL anomaly detection  

Example:
- Observed TTL = 122  
- Likely initial TTL = 128  
- Approximate hops = 6  

---

## 8. Record-Route Option

Rarely used today.

Allows routers to record path in packet header:
```bash
ping -R

Mostly disabled due to:
- Performance overhead  
- Information disclosure risk  

Can assist attackers in network mapping if enabled.

---

## 9. Traceroute Mechanism (TTL Manipulation)

Traceroute works by:
1. Sending packet with TTL = 1  
2. Router drops packet  
3. Router replies with ICMP Time Exceeded  
4. TTL increases incrementally  
5. Final host replies (RST, ICMP, or SYN-ACK)  

**Security relevance:**
- Reconnaissance  
- Firewall path discovery  
- Network topology mapping  

---

## 10. TCP Header Deep Dive

**Key fields:**

| Field            | Purpose             |
|------------------|---------------------|
| Source Port      | Sending application |
| Destination Port | Target service      |
| Sequence Number  | Data ordering       |
| ACK Number       | Acknowledgment      |
| Window Size      | Flow control        |
| Checksum         | Error detection     |
| Flags            | Session state       |

### Sequence Numbers & Security

Predictable sequence numbers enable:
- TCP hijacking  
- Blind spoofing  

Modern TCP stacks randomize Initial Sequence Numbers (ISNs) to mitigate this risk.

---

## 11. UDP Behavior in Traceroute

- Linux/Unix `traceroute` → Sends UDP packets to high ports  
- Destination replies with **ICMP Port Unreachable**  
- Windows `tracert` → Uses **ICMP Echo Requests**

---

## 12. Blind Spoofing

Blind spoofing:
- Attacker cannot see responses  
- Spoofs source IP  
- Guesses sequence numbers  
- Attempts packet injection  

**Mitigated by:**
- ISN randomization  
- Stateful firewalls  
- Modern TCP stack protections  

---

## 13. Common TCP/UDP Attacks

| Attack                 | Protocol |
|------------------------|----------|
| SYN Flood              | TCP      |
| UDP Flood              | UDP      |
| Fragmentation Evasion  | IP       |
| IP Spoofing            | IP       |
| Session Hijacking      | TCP      |
| DNS Amplification      | UDP      |
| Smurf Attack           | ICMP     |
| Blind Spoofing         | TCP      |

---

## 14. Forensic & Detection Considerations

When analyzing traffic, look for:
- TTL inconsistencies  
- Sequential IP ID patterns  
- SYN packets without corresponding ACK  
- Unexpected RST packets  
- Abnormal fragmentation  
- Port scanning patterns  

---

## CDSA-Level Questions

1. Why is TCP more secure than UDP?  
2. How does TCP prevent data loss?  
3. What is the purpose of the IP ID field?  
4. How does traceroute work?  
5. What is blind spoofing?  
6. Why is ISN randomization important?  
7. What is a SYN flood?  
8. How can fragmentation bypass IDS?
