# Distributed Denial of Service (DDoS)

## What a DDoS Attack Is

A Distributed Denial of Service (DDoS) attack attempts to disrupt the availability of a service by overwhelming it with traffic from many sources at once.

**Key characteristics:**
- Traffic originates from multiple compromised systems  
- These systems form a botnet  
- The goal is service exhaustion, not data theft (though DDoS may be used as cover for other attacks)  

**Core security principle affected:**  
- **Availability** (CIA Triad)

---

## DoS vs DDoS

- **DoS:** Single source  
- **DDoS:** Many distributed sources  

> DDoS attacks are harder to block, harder to attribute, and operate at much larger scale.

---

## Core Components of a DDoS Attack

### 1. Attacker
- Controls and coordinates the attack  
- Chooses timing, target, and method  

---

### 2. Botnet
- Network of compromised devices:
  - PCs and servers  
  - IoT devices (cameras, routers, sensors)  
- Often infected via:
  - Weak/default credentials  
  - Unpatched vulnerabilities  

---

### 3. Victim
Targets may include:
- Websites  
- APIs  
- DNS services  
- Network infrastructure  

**Impact on victims:**
- Bandwidth exhaustion  
- CPU/memory exhaustion  
- Connection table exhaustion  

---

## How a DDoS Attack Works (Simplified Flow)

1. Attacker issues command to the botnet  
2. Bots simultaneously send traffic to the target  
3. Target resources are exhausted  
4. Legitimate users experience:
   - Severe latency  
   - Errors  
   - Complete outage  

> **Important note:**  
> Malicious traffic may appear legitimate at the protocol level, complicating detection.

---

## Common DDoS Attack Categories

### Volumetric Attacks
- Flood bandwidth with massive traffic  
- Examples:
  - UDP floods  
  - Amplification attacks  

**Goal:** Saturate network links

---

### Protocol Attacks
- Exploit protocol weaknesses  
- Examples:
  - SYN floods  
  - Fragmentation attacks  

**Goal:** Exhaust server or network resources

---

### Application-Layer Attacks
- Target specific services (HTTP, APIs)  
- Lower traffic volume but high impact  
- Mimic normal user behavior  

**Goal:** Exhaust application resources  
**Detection difficulty:** Highest

---

## Real-World Impact

DDoS attacks can cause:
- Revenue loss (especially for online services)  
- Reputational damage  
- Operational disruption  
- Regulatory or SLA violations  

**Advanced attacker tactic:**  
Use DDoS as a smokescreen while launching:
- Data breaches  
- Malware deployment  
- Lateral movement  

---

## Why IoT Makes DDoS Worse

- IoT devices are:
  - Always online  
  - Rarely patched  
  - Deployed at scale  

> **Defender takeaway:**  
> IoT insecurity fuels internet-scale botnets and DDoS attacks.

---

## Detection (SOC Perspective)

**Indicators of DDoS:**
- Sudden traffic spikes  
- Traffic from unusual geolocations  
- Repeated identical requests  
- Service degradation without corresponding application errors  

**Key monitoring sources:**
- Network flow data  
- Firewall metrics  
- Load balancer statistics  
- Application error rates  

---

## Mitigation & Defense Strategies

### Preventive Measures
- Rate limiting  
- Network segmentation  
- Harden exposed services  
- Reduce attack surface  

---

### Detection & Response
- Traffic baselining  
- Automated alerts  
- Rapid escalation procedures  

---

### DDoS Mitigation Services
- Traffic scrubbing centers  
- CDN-based protection  
- Anycast routing  

**Goal:**  
Absorb or filter malicious traffic before it reaches the target.

---

## Roles & Responsibilities

- **Network & Security Teams**
  - Detection and mitigation  

- **SOC Analysts**
  - Identify attack patterns  
  - Escalate and coordinate response  

- **Management**
  - Define risk tolerance and preparedness decisions  
