# Module 3 – INTRODUCTION TO NETWORKING  
## 3.13 Networking Key Terminology – Protocols You Must Know (CDSA-Focused Notes)

Networking is full of terminology, and no one memorizes everything.  
What matters for a defensive analyst is understanding:

- What the protocol does  
- At which layer it operates  
- Why attackers abuse it  
- How defenders monitor it  

Below is a structured, security-focused breakdown of the essential terms.

---

## 1. Wireless Security Protocols

| Protocol | Purpose                   | Security Note                 |
|----------|---------------------------|-------------------------------|
| WEP      | Early Wi-Fi encryption    | Broken – easily cracked       |
| WPA      | Improved wireless security| WPA2/WPA3 recommended         |
| TKIP     | Temporary Wi-Fi encryption| Deprecated                    |
| EAP      | Authentication framework  | Used in WPA Enterprise        |
| LEAP     | Cisco wireless auth       | Weak, deprecated              |
| PEAP     | Encrypted auth tunnel     | Common in enterprise Wi-Fi    |

**CDSA Tip:**  
If you see **WEP** or **TKIP** in an assessment → immediate security finding.

---

## 2. Remote Access & Administration

| Protocol | Purpose                     | Security Concern            |
|----------|-----------------------------|-----------------------------|
| SSH      | Secure remote login         | Brute force, key misuse    |
| RSH      | Remote shell (unencrypted)  | Insecure, deprecated       |
| TACACS+  | Centralized AAA             | Network device control     |
| VPN      | Secure remote access       | Split tunnel risks         |
| IPsec    | Encrypted network traffic  | Site-to-site VPNs          |
| PPTP     | Legacy VPN protocol        | Weak, insecure             |
| IKE      | Negotiates IPsec tunnels   | Brute-force target         |

**Analysts monitor:**
- Failed SSH logins  
- VPN connection anomalies  
- AAA misconfigurations  

---

## 3. Web & Application Protocols

| Term   | Purpose                         |
|--------|---------------------------------|
| HTTP   | Web traffic                     |
| AJAX   | Dynamic web requests            |
| ISAPI  | Web server extension interface  |
| URI    | Resource identifier             |
| URL    | Location of web resource        |
| CRLF   | Line termination characters     |

**Security relevance:**
- HTTP → Injection attacks  
- CRLF → Response splitting  
- URL manipulation → SSRF  
- AJAX → XSS risk  

---

## 4. File Sharing & Transfer

| Protocol | Purpose           | Security Concern           |
|----------|-------------------|----------------------------|
| FTP      | File transfer     | Plaintext credentials     |
| SMB      | Windows file share| Lateral movement          |
| NFS      | Unix file sharing | Misconfigured exports     |

SMB is heavily abused in:
- Pass-the-Hash  
- NTLM relay  
- Ransomware propagation  

---

## 5. Email Protocols

| Protocol | Purpose       |
|----------|---------------|
| SMTP     | Send email    |
| PGP      | Encrypt email |

**Security relevance:**
- SMTP misconfiguration → spoofing  
- PGP → secure communications  

---

## 6. Network Management & Monitoring

| Protocol | Purpose                     |
|----------|-----------------------------|
| SNMP     | Manage network devices      |
| NTP      | Time synchronization        |
| CDP      | Cisco device discovery      |
| SMS      | System management           |
| MBSA     | Windows vulnerability scan |

**Security notes:**
- SNMP v1/v2 use plaintext community strings  
- Incorrect NTP breaks log correlation  

---

## 7. Routing Protocols

| Protocol | Type               | Notes             |
|----------|--------------------|-------------------|
| RIP      | Distance-vector    | Simple, legacy    |
| OSPF     | Link-state         | Widely used       |
| IGRP     | Cisco proprietary  | Legacy            |
| EIGRP    | Hybrid             | Cisco             |
| BGP      | Inter-domain       | Internet backbone |

**Security relevance:**
- Route hijacking  
- OSPF spoofing  
- Rogue routing advertisements  

---

## 8. Layer 2 & Switching

| Protocol | Purpose                     |
|----------|-----------------------------|
| VLAN     | Logical network segmentation|
| VTP      | VLAN management             |
| STP      | Prevent Layer 2 loops       |

**Security relevance:**
- VLAN hopping  
- STP manipulation  
- Misconfigured trunk ports  

---

## 9. High Availability & Redundancy

| Protocol | Purpose                    |
|----------|----------------------------|
| HSRP     | Cisco router redundancy    |
| VRRP     | Vendor-neutral redundancy  |

Used to ensure gateway availability.

---

## 10. Industrial & Special Protocols

| Protocol | Purpose                         |
|----------|---------------------------------|
| SCADA    | Industrial control systems      |
| SIP      | Voice/video signaling           |
| VoIP     | Voice over IP                  |
| NNTP     | Newsgroups                     |
| GRE      | Tunnel encapsulation           |

**Security note:**  
SCADA environments are high-impact, high-risk targets.

---

## 11. Encryption & Security Protocols

| Protocol | Purpose                  |
|----------|--------------------------|
| IPsec    | Network encryption       |
| PGP      | File/email encryption    |
| IKE      | IPsec negotiation        |

---

## 12. Addressing & Translation

| Protocol | Purpose                     |
|----------|-----------------------------|
| NAT      | Private-to-public mapping  |

**Security implications:**
- Hides internal structure  
- Breaks end-to-end visibility  
- Complicates forensic logging  

---

## 13. How to Study This for CDSA

Do **not** memorize blindly.  
Group protocols by:

- OSI layer  
- Function (Routing, Auth, Management)  
- Attack surface  
- Monitoring relevance  

Ask:
- Is it encrypted?  
- Is it authenticated?  
- Is it internal-only?  
- Can attackers pivot through it?  

---

## 14. Common Interview Questions

1. What protocol does SMB use?  
2. Difference between RIP and OSPF?  
3. Why is SNMP dangerous?  
4. What is VLAN?  
5. Why is PPTP insecure?  
6. What does STP prevent?  
7. Difference between URI and URL?  

---

## 15. CDSA Takeaway

These protocols represent:

- Entry points  
- Lateral movement channels  
- Monitoring targets  
- Segmentation controls  
- Encryption layers  

Understanding them enables you to:

- Read packet captures  
- Interpret firewall rules  
- Analyze SIEM alerts  
- Reconstruct attack chains  
