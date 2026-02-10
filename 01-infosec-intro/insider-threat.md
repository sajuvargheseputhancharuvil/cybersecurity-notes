# Insider Threat

## What an Insider Threat Is

An Insider Threat originates from individuals who already have authorized access to an organization’s systems, data, or facilities (employees, contractors, partners).

**Key distinction:**
- External attackers break in  
- Insiders abuse legitimate access  

**Why it’s dangerous:**
- Activity blends with normal behavior  
- Insiders know where sensitive data lives  
- Perimeter defenses offer limited protection  

**Security principles affected:**
- Confidentiality  
- Integrity  
- Availability  

---

## Types of Insider Threats

### 1. Malicious Insiders
**Intentional harm**

**Motivations:**
- Financial gain  
- Revenge or grievance  
- Espionage  

**Actions:**
- Data theft  
- Sabotage  
- Fraud  

---

### 2. Negligent Insiders
**Unintentional harm**

**Causes:**
- Poor security awareness  
- Carelessness  
- Falling for phishing  

**Examples:**
- Sending data to the wrong recipient  
- Reusing passwords  
- Bypassing controls “for convenience”  

---

### 3. Compromised Insiders
- Credentials stolen by external attackers  
- Attacker operates as a legitimate user  

**Common sources:**
- Phishing  
- Malware  
- Credential reuse  

> **SOC reality:**  
> Many “insider” incidents are actually external attackers using insider identities.

---

## Why Insider Threats Are Hard to Detect

- Legitimate access masks malicious intent  
- Actions often occur during normal business hours  
- Insiders understand controls and blind spots  
- Organizations over-focus on external threats  

> **Key takeaway:**  
> Trust enables productivity — and risk.

---

## Insider Threat Lifecycle (Kill Chain)

### 1. Motivation
Triggered by:
- Financial stress  
- Job dissatisfaction  
- External coercion  
- Opportunity  

---

### 2. Planning
- Evaluating access rights  
- Identifying high-value assets  
- Assessing detection mechanisms  

---

### 3. Preparation
- Gathering tools or data  
- Learning how to bypass controls  
- Testing boundaries  

---

### 4. Execution
- Data exfiltration  
- System sabotage  
- Unauthorized sharing  

---

### 5. Concealment
- Using others’ credentials  
- Blending activity with routine tasks  
- Log tampering (where possible)  

---

## Impact of Insider Threats

### Financial Impact
- Direct theft  
- Incident response and recovery costs  
- Regulatory fines  

### Operational Impact
- System downtime  
- Loss of critical data  
- Disrupted services  

### Reputational Impact
- Loss of customer trust  
- Long-term brand damage  

### Strategic Impact
- Intellectual property theft  
- Loss of competitive advantage  
- Long-term business harm  

---

## Legal & Regulatory Consequences

Insider incidents often trigger:
- Data protection violations  
- Regulatory investigations  
- Heavy fines  
- Lawsuits (customers, partners, shareholders)  

> **Key point:**  
> Regulators expect preventive and detective controls — not excuses.

---

## Detection (SOC Perspective)

### Behavioral Indicators
- Access outside normal patterns  
- Sudden data hoarding  
- Unusual privilege use  
- Access to systems unrelated to role  
- Large or repeated data transfers  

### Key Telemetry
- Authentication logs  
- File access and modification logs  
- Privileged activity logs  
- Endpoint behavior  
- Cloud access patterns  

> Effective detection relies on **context**, not single alerts.

---

## Prevention & Mitigation

### Access Management
- Least privilege  
- Role-based access  
- Regular access reviews  
- Immediate deprovisioning on role change or exit  

---

### User Behavior Analytics (UBA / UEBA)
- Baseline normal behavior  
- Detect anomalies over time  
- Critical for insider threat detection  

---

### Monitoring & Logging
- Centralized logging  
- Long retention for investigations  
- Tamper-resistant logs  

---

### Security Awareness
- Reduce negligent insider risk  
- Encourage reporting  
- Clear policies and consequences  

---

### Culture & Process
- Separation of duties  
- Mandatory vacations (for sensitive roles)  
- Strong HR–Security collaboration  

---

## Role of Testing & Red Teams

- Insider threat simulations  
- Privilege abuse testing  
- Process bypass attempts  
- Social engineering scenarios  

**Blue-team benefit:**
- Reveals trust gaps  
- Improves detection logic  
- Validates governance controls
