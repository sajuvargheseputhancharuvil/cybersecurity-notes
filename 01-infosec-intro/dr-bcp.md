# Disaster Recovery (DR) & Business Continuity (BC)

## Why DR & BC Matter

Disaster Recovery (DR) and Business Continuity (BC) together define an organization’s **resilience** — its ability to withstand disruption and continue operating.

**Incidents include:**
- Cyberattacks (ransomware, destructive malware)  
- Infrastructure failures  
- Natural disasters  
- Human or physical incidents  

**Poor DR/BC leads to:**
- Prolonged downtime  
- Data loss  
- Regulatory penalties  
- Loss of customer trust  

---

## Disaster Recovery (DR)

### What DR Focuses On
Disaster Recovery is **technology-centric**.

**Primary objective:**  
Restore critical IT systems and data after a disruptive event.

**DR answers:**
- How do we recover systems?  
- How fast can we restore them?  
- How much data loss is acceptable?  

---

### Core DR Components
- **Backups**  
  - Regular, tested, and protected from tampering  
- **Replication**  
  - Data mirrored to alternate locations  
- **Failover**  
  - Switching operations to backup systems or sites  
- **Recovery procedures**  
  - Step-by-step restoration playbooks  

---

### Key DR Metrics (Exam-Critical)

- **RTO (Recovery Time Objective)**  
  - Maximum acceptable downtime  

- **RPO (Recovery Point Objective)**  
  - Maximum acceptable data loss (time-based)  

**Example:**  
RTO = 4 hours, RPO = 15 minutes  
→ Systems must be restored within 4 hours with no more than 15 minutes of data loss.

---

## Business Continuity (BC)

### What BC Focuses On
Business Continuity is **business-centric**.

**Primary objective:**  
Keep essential operations running during and after disruption.

**BC answers:**
- How does the business function if systems are unavailable?  
- What alternative processes are needed?  

---

### Core BC Components
- Identification of critical business functions  
- Alternative workflows and procedures  
- Workforce continuity (remote work, role substitution)  
- Supplier and dependency planning  
- Temporary facilities or relocation strategies  

> **Key idea:**  
> DR restores systems.  
> BC keeps the business operating with or without systems.

---

## DR vs BC (Clear Distinction)

| Aspect      | Disaster Recovery (DR) | Business Continuity (BC) |
|-------------|-------------------------|---------------------------|
| Focus       | IT systems & data       | Business operations       |
| Scope       | Technical               | Organizational            |
| Timeline    | After disruption        | During & after disruption |
| Ownership   | IT / Security           | Business leadership       |

> DR and BC complement each other — neither replaces the other.

---

## Building an Effective DR/BC Strategy

### 1. Risk Assessment
- Identify threats that could disrupt operations  
- Evaluate likelihood and impact  

---

### 2. Business Impact Analysis (BIA)
- Identify critical functions  
- Determine:
  - RTOs  
  - RPOs  
- Prioritize recovery efforts  

---

### 3. Strategy Design
**DR strategies:**
- Backup types  
- Replication models  
- Failover architectures  

**BC strategies:**
- Manual workarounds  
- Remote operations  
- Alternative suppliers  

---

### 4. Documentation
- Clear, accessible plans  
- Defined roles and responsibilities  
- Contact lists and escalation paths  

---

### 5. Testing & Exercises

> **Testing is mandatory, not optional.**

**Types:**
- Tabletop exercises  
- Walkthroughs and decision-making drills  
- Simulation tests  
- Partial or full failover  
- Live recovery tests  
- Real restoration from backups  

**Frequency:**
- Often annual or regulatory-driven  
- More frequent for critical systems  

---

## Responsibility & Governance

**Ownership:**
- Business Continuity Manager or equivalent  
- Strategic oversight by executive leadership  

**Collaboration required with:**
- IT & Infrastructure teams  
- Security & SOC  
- Operations  
- Compliance & Legal  
- Senior management  

---

## Role of Security & Penetration Testing

- Identify weaknesses that could:
  - Prevent recovery  
  - Compromise backups  
  - Break failover mechanisms  
- Validate assumptions in DR/BC plans  
- Feed real attack scenarios into planning
