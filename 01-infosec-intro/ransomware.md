# Ransomware

## What Ransomware Is

Ransomware is malicious software that:
- Gains access to a system or network  
- Encrypts data (files, databases, backups)  
- Demands payment (usually cryptocurrency) for a decryption key  

**Primary security principle affected:**  
- **Availability** (often **Integrity** as well)

> **Key reality:**  
> Paying the ransom does not guarantee recovery and often increases future risk.

---

## Attacker Motivation

- Financial extortion is the dominant motive  
- Common targets:
  - Enterprises  
  - Healthcare  
  - Government  
  - Education  
  - Individuals  

**Why ransomware is effective:**
- Data is mission-critical  
- Downtime pressure forces quick decisions  
- Recovery is costly without strong backups  

---

## How Ransomware Works (Attack Lifecycle)

### 1. Initial Access
**Common entry points:**
- Phishing emails (malicious links/attachments)  
- Exploited vulnerabilities (unpatched systems)  
- Compromised credentials  
- Remote services (RDP, VPN misconfigurations)  

---

### 2. Execution & Persistence
- Malware installs and may:
  - Disable security tools  
  - Establish persistence  
  - Communicate with command-and-control (C2)  

---

### 3. Privilege Escalation & Lateral Movement
- Expands access across the network  
- Targets:
  - File servers  
  - Domain controllers  
  - Backup systems  

> **Critical insight:**  
> Modern ransomware often behaves like an APT before encryption.

---

### 4. Data Encryption
- Uses strong cryptography  
- Files become unreadable without keys  
- Often deletes or encrypts backups first  

---

### 5. Ransom Demand
- Ransom note with:
  - Payment instructions  
  - Deadline  
  - Threats (data deletion or public leak)  

**No guarantees:**
- Decryption keys may not work  
- Attackers may disappear  
- Victims may be re-targeted  

---

## Real-World Pattern (Why Patching Matters)

- Large-scale outbreaks often exploit known vulnerabilities  
- Systems missing security updates are common victims  
- Critical infrastructure has been heavily impacted  

> **Exam takeaway:**  
> Unpatched systems + exposed services = ransomware risk

---

## Impact of Ransomware

### Operational Impact
- System outages  
- Business shutdowns  
- Loss of essential services  

### Financial Impact
- Ransom payments  
- Recovery and remediation costs  
- Legal and regulatory penalties  

### Data Impact
- Permanent data loss if backups fail  
- Data integrity concerns  
- Double extortion (encrypt + leak)  

### Reputational Impact
- Loss of customer trust  
- Long-term brand damage  

### Broader Risk
- Downstream impact on partners and users  
- Paying ransoms fuels the cybercrime ecosystem  

---

## Detection (SOC Perspective)

**Common indicators:**
- Sudden mass file modifications  
- Unusual file extensions  
- Spikes in CPU/disk usage  
- Disabled backups or security tools  
- Suspicious privilege escalation  
- C2 communication patterns  

**Key log sources:**
- Endpoint telemetry  
- File integrity monitoring  
- Authentication logs  
- Network traffic  

---

## Prevention & Mitigation

### Preventive Controls
- Regular patching  
- Phishing awareness training  
- MFA on remote access  
- Least privilege enforcement  
- Network segmentation  

---

### Backup Strategy (Critical)
- Offline or immutable backups  
- Regular backup testing  
- Segregated backup access  

> **Golden rule:**  
> Backups are the strongest ransomware defense — if protected properly.

---

### Incident Response
- Isolate affected systems immediately  
- Preserve evidence  
- Disable compromised accounts  
- Initiate recovery from clean backups  
- Communicate through predefined IR plans  

---

## Role of DR & BC

- Ransomware frequently triggers:
  - Disaster Recovery (DR)  
  - Business Continuity (BC) plans  

> Strong DR/BC reduces pressure to pay ransom.
