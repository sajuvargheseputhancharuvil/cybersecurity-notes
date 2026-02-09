# Network Security

## What Network Security Is

Network Security focuses on protecting:
- Network infrastructure  
- Data in transit  
- Connected devices and services  

from:
- External attackers  
- Internal misuse or compromise  

Network security is a core pillar of Information Security because most attacks either:
- Travel through the network, or  
- Exploit network exposure to reach systems.

---

## Scope of Network Security

Network security applies to:

- Internal corporate networks  
- Internet-facing services  
- Cloud and hybrid environments  
- Remote access (VPNs, remote workers)  
- IoT and mobile-connected devices  

> **Key idea:**  
> If it communicates, it must be secured.

---

## Core Elements of Network Security

### Firewalls
**Purpose:** Traffic control and segmentation

- Act as a barrier between trusted and untrusted networks  
- Enforce rules based on:
  - IP addresses  
  - Ports  
  - Protocols  
  - Application awareness (NGFWs)  

> ⚠️ **Exam & interview reality:**  
> Firewalls are necessary but insufficient. Misconfigurations are a common attack path.

---

### IDS / IPS (Intrusion Detection & Prevention Systems)
**Purpose:** Detect and/or block malicious activity

- **IDS**  
  - Detects suspicious traffic  
  - Generates alerts  
- **IPS**  
  - Actively blocks detected threats  

**Used for:**
- Known attack signatures  
- Behavioral anomalies  

**SOC relevance:**
- Alerts often feed into SIEM  
- False positives are a constant challenge

---

### Virtual Private Networks (VPNs)
**Purpose:** Secure remote communication

- Encrypt traffic over untrusted networks  
- Common use cases:
  - Remote employees  
  - Secure site-to-site connections  

**Blue team concerns:**
- Stolen credentials  
- Weak authentication  
- Overly broad access

---

### Access Control Mechanisms
**Purpose:** Restrict who can access what

Includes:
- Authentication (identity verification)  
- Authorization (permission enforcement)  

Examples:
- Network ACLs  
- Role-based access  
- Network segmentation  

> **Key principle:**  
> Access should follow least privilege.

---

### Encryption Technologies
**Purpose:** Protect confidentiality and integrity of data

- **In transit:** TLS, VPN encryption  
- **At rest:** Encrypted storage, encrypted databases  

**Security takeaway:**  
Encryption limits attacker impact even after compromise.

---

## Defense Is Layered (Security Reality)

No single control is sufficient:

- Firewalls can be bypassed  
- VPNs can be abused  
- Credentials can be stolen  
- Zero-day exploits exist  

**Therefore:**  
Network security must assume eventual compromise and focus on **detection and containment**, not only prevention.

---

## Network Threat Landscape

**Common attacker motivations:**
- Financial gain (ransomware, fraud)  
- Espionage (state-sponsored actors)  
- Disruption (hacktivism)  

**Impact of a network breach:**
- Financial loss  
- Operational downtime  
- Reputational damage  
- Legal and regulatory consequences  

**Why risk is increasing:**
- Cloud adoption  
- Remote work  
- IoT proliferation  
- Larger, flatter networks

---

## Responsibility for Network Security

### Primary Ownership
- Network Security Team (under IT / Security)  
- Typically reports into:
  - Network Security Manager  
  - CISO (strategic oversight)  

### Core Responsibilities
- Design secure network architecture  
- Configure and maintain security devices  
- Monitor network traffic  
- Respond to network-based incidents  
- Enforce network security policies  

---

## Testing Network Security

### Why Testing Matters
- Validates real-world effectiveness  
- Finds gaps that policies don’t reveal  
- Simulates attacker behavior  

### Who Performs Testing
- Internal penetration testing teams  
- External consultants / MSSPs  
- Authorized ethical hackers  

**Blue team usage:**
- Improve detections  
- Close exposed attack paths  
- Validate control effectiveness
