# Network Security

Network security focuses on protecting:
- Data  
- Devices  
- Applications  
- Infrastructure  

The ultimate goal is to preserve the **CIA Triad**.

---

## 1. CIA Triad (Core Security Principles)

| Principle        | Meaning                                      |
|------------------|----------------------------------------------|
| Confidentiality  | Only authorized users can access data        |
| Integrity        | Data is accurate and not altered             |
| Availability     | Systems and services remain accessible       |

Every security control in networking supports one or more of these principles.

**Examples:**
- Firewall → Confidentiality (and Availability)  
- Hash validation → Integrity  
- Redundancy → Availability  

**CDSA Insight:**  
Most security incidents involve a violation of at least one CIA principle.

---

## 2. Firewalls

A firewall is a device (hardware or software) that:
- Monitors network traffic  
- Applies rules  
- Allows or blocks packets  

Think of it as a gatekeeper controlling traffic entering or leaving the network.

### How Firewalls Work

Firewalls analyze:
- Source IP  
- Destination IP  
- Source Port  
- Destination Port  
- Protocol  

Based on configured rules (ACLs or policies), they can:
- Allow traffic  
- Block traffic  
- Log events  
- Generate alerts  

**Typical placement:**  
`Internet → Firewall → Internal Network`

---

## 3. Types of Firewalls

### 1. Packet Filtering Firewall
- Operates at Layer 3 & 4  
- Examines IPs, ports, protocols  
- Stateless  

**Pros:**
- Fast  
- Lightweight  

**Cons:**
- No session awareness  

---

### 2. Stateful Inspection Firewall
- Tracks connection state  
- Understands sessions  
- Allows return traffic for established connections  

More secure than simple packet filtering.

---

### 3. Application Layer Firewall (Proxy)
- Operates at Layer 7  
- Inspects payload content  
- Can filter malicious application requests  

**Example:**  
Blocking suspicious SQL injection patterns in HTTP traffic.

Used in:
- Web proxies  
- Secure gateways  

---

### 4. Next-Generation Firewall (NGFW)
Modern firewalls that combine:
- Stateful inspection  
- Deep Packet Inspection (DPI)  
- IDS/IPS  
- Application awareness  
- Encrypted traffic inspection  

Enterprise standard for perimeter security.

---

### Security Perspective

Firewalls:
- Enforce segmentation  
- Reduce attack surface  
- Implement least privilege  

**But:**  
Firewall misconfiguration is a common root cause of breaches.

---

## 4. IDS vs IPS

Both monitor for malicious activity.

| System | Action             |
|--------|--------------------|
| IDS    | Detects & alerts   |
| IPS    | Detects & blocks   |

### Detection Methods

**Signature-Based Detection**
- Matches known attack patterns  
- Fast and accurate for known threats  
- Weakness: Cannot detect zero-day attacks  

**Anomaly-Based Detection**
- Detects deviations from baseline behavior  
- Can detect unknown threats  
- Weakness: Higher false positives  

### IDS/IPS Types

**Network-Based (NIDS/NIPS)**
- Monitors traffic between systems  
- Placed in network path  
- Common in data centers and enterprise cores  

**Host-Based (HIDS/HIPS)**
- Installed on endpoints  
- Monitors system logs and behavior  
- Detects local compromise  

**Common placements:**
- Behind firewalls  
- In DMZ  
- On critical servers  

---

## 5. DMZ (Demilitarized Zone)

A DMZ is a segmented network zone that:
- Hosts public-facing services  
- Is isolated from the internal LAN  

**Examples:**
- Web servers  
- Mail servers  

**Purpose:**  
If compromised, the internal network remains protected.

---

## 6. Defense in Depth

No single security control is sufficient.

Layered security includes:
- Firewalls  
- IDS/IPS  
- Antivirus / EDR  
- Access controls  
- Network segmentation  

This approach:
- Slows attackers  
- Increases detection opportunities  
- Reduces single points of failure  

---

## 7. Best Practices (Operational Focus)

| Practice             | Why It Matters                     |
|----------------------|-------------------------------------|
| Least Privilege      | Allow only necessary traffic        |
| Regular Updates      | Patch vulnerabilities               |
| Log Monitoring       | Detect early signs of attack        |
| Layered Security     | Prevent single point of failure     |
| Penetration Testing | Validate defenses                   |

---

## 8. Security Monitoring Perspective (CDSA Critical)

As a defensive analyst, you will:
- Review firewall logs  
- Investigate IDS alerts  
- Correlate network events  
- Analyze blocked connections  
- Identify anomalous traffic patterns  

**Important:**  
Alerts alone are not enough. Correlation is key.

---

## 9. Common Real-World Issues
- Firewall rules too permissive  
- IDS signatures outdated  
- Logging disabled  
- No monitoring team  
- IPS blocking legitimate traffic (false positives)  

---

## 10. Interview Questions to Prepare

1. What is the CIA triad?  
2. Difference between IDS and IPS?  
3. What is stateful inspection?  
4. What is a DMZ?  
5. Why is defense-in-depth important?  
6. What is least privilege in firewall rules? 
