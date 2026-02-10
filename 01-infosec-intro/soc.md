# Security Operations Center (SOC)

## What a SOC Is

A Security Operations Center (SOC) is a centralized function responsible for continuous monitoring, detection, analysis, and response to cybersecurity threats and incidents across an organization.

**Core mission:**
- Detect threats early  
- Respond fast and effectively  
- Reduce attacker dwell time  
- Protect Confidentiality, Integrity, and Availability (CIA)  

> Think of the SOC as the operational heartbeat of the Blue Team.

---

## Core Functions of a SOC

### Continuous Monitoring
- 24/7 visibility across:
  - Endpoints  
  - Networks  
  - Cloud services  
  - Identity systems  
- Aggregates logs, alerts, and telemetry  

**Primary tools:**
- SIEM  
- EDR / XDR  
- IDS / IPS  
- Network and cloud logs  

---

### Detection & Analysis
- Identify suspicious or malicious activity  
- Correlate signals across multiple sources  
- Separate false positives from real incidents  

> **Key goal:**  
> Turn raw alerts into actionable intelligence.

---

### Incident Response
- Investigate confirmed incidents  
- Contain threats quickly  
- Coordinate eradication and recovery  
- Preserve evidence for lessons learned or legal needs  

---

### Threat Hunting
- Proactively search for:
  - Undetected attackers  
  - Dormant malware  
  - Credential abuse  
- Goes beyond alerts  

> **Value:**  
> Finds what automated tools miss.

---

### Reporting & Metrics
- Track:
  - Incident trends  
  - Detection gaps  
  - Response times  
- Feed insights to leadership and the CISO  

---

## SOC Team Structure & Roles

### SOC Analysts (Tiered Model)

**Tier 1 – Alert Triage**
- First line of defense  
- Validate alerts  
- Perform basic investigation  
- Escalate when needed  

**Focus:** Speed and accuracy

---

**Tier 2 – Incident Analysis**
- Handle complex investigations  
- Correlate events across systems  
- Guide containment actions  
- Mentor Tier 1 analysts  

**Focus:** Depth and context

---

**Tier 3 – Incident Response / Advanced Analysis**
- Manage critical incidents  
- Perform advanced forensics  
- Lead eradication and recovery  
- Often overlap with Incident Responders  

**Focus:** High-impact decision-making

---

### SOC Manager
- Oversees SOC operations  
- Manages staffing, workflows, and SLAs  
- Ensures playbooks are followed  
- Reports status and risk to leadership  

---

## Supporting Roles

**Threat Hunters**
- Proactive detection specialists  
- Hypothesis-driven investigations  
- Improve detections based on findings  

**Security Engineers / Architects**
- Maintain SOC tooling  
- Build integrations and pipelines  
- Improve visibility and automation  

---

## SOC Purpose (Why It Exists)

### Early Threat Detection
- Faster detection = less damage  
- Reduces attacker dwell time  

---

### Rapid & Coordinated Response
- Structured incident handling  
- Minimizes blast radius  
- Protects business operations  

---

### Business Continuity
- Prevents minor incidents from becoming crises  
- Keeps systems and services running  

---

### Security Posture Improvement
- Continuous feedback loop  
- Informs control tuning and investment decisions  

---

## SOC Governance & Collaboration

- Typically reports under the CISO  
- Works closely with:
  - IT (patching, remediation)  
  - Engineering (fix root causes)  
  - Legal & Compliance (regulatory impact)  
  - Management (risk communication)  

> SOC success depends on cross-team cooperation.

---

## Key SOC Metrics (CDSA-Relevant)

- Time to Detect (TTD)  
- Time to Respond (TTR)  
- Dwell time  
- Alert fidelity (true vs false positives)  
- Incident recurrence rate  
- Coverage gaps  

---

## SOC vs Other Security Functions

| Function     | Focus                        |
|--------------|------------------------------|
| SOC          | Detect & respond (real-time) |
| Blue Team    | Overall defense strategy     |
| Red Team     | Attack simulation            |
| Purple Team  | Red–Blue collaboration       |
| CISO         | Strategy & risk ownership    |
