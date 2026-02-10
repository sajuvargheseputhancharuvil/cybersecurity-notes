# Red Team

## What a Red Team Is

A Red Team is a group of security professionals that simulate real-world adversaries to test an organization’s defenses end-to-end.

**Key traits:**
- Adversary-focused, not tool-focused  
- Holistic scope: technology, people, and physical security  
- Operates covertly to measure true detection and response  

> **Red Team ≠ vulnerability scan or short penetration test.**

---

## Why Red Teams Exist

Traditional testing often answers:
- “Is this system vulnerable?”

Red Teams answer:
- “Can an attacker achieve real objectives without being detected?”

They validate:
- Detection capability  
- Incident response effectiveness  
- Human resilience  
- Assumptions in security design  

---

## Scope of Red Team Operations

Red Teams test multiple attack surfaces simultaneously:

- **Technical**  
  - Networks, endpoints, applications, cloud  

- **Human**  
  - Phishing, pretexting, social engineering  

- **Physical**  
  - Building access, badge controls, tailgating  

- **Process**  
  - Alert handling, escalation, decision-making  

- **Supply Chain**  
  - Third-party exposure and trust paths  

---

## Red Team Composition (Skill Mix)

A mature Red Team includes specialists such as:
- Offensive operators (network/application exploitation)  
- Social engineers (phishing, pretexting)  
- Physical testers (facility access)  
- Infrastructure & tooling engineers  
- Campaign lead / strategist  

> This mirrors how real threat actor teams operate.

---

## How Red Team Engagements Run

### 1. Planning & Objectives
- Define business-relevant goals, such as:
  - Access sensitive data  
  - Compromise domain admin  
  - Evade detection for a defined period  
- Establish rules of engagement and safety boundaries  

---

### 2. Reconnaissance
- Open-source intelligence (OSINT)  
- Digital footprint analysis  
- Employee roles and workflows  
- Third-party dependencies  

**Goal:** Identify realistic entry points attackers would use.

---

### 3. Initial Access
- Phishing or social engineering  
- Exploiting exposed services  
- Credential abuse  
- Physical entry (where in scope)  

---

### 4. Lateral Movement & Privilege Escalation
- Expand access quietly  
- Target identity systems  
- Avoid noisy techniques  

> **Key behavior:**  
> Low-and-slow to evade detection.

---

### 5. Objective Achievement
- Simulated data access or exfiltration  
- Control over critical systems  
- Persistence demonstration  

---

### 6. Reporting & Debrief
- Detailed attack narrative  
- What worked / what failed  
- Where detection succeeded or failed  
- Actionable remediation guidance  

Delivered to senior stakeholders (CISO, leadership).

---

## What Red Teams Measure

- Time to detection  
- Quality of alerts  
- Analyst response accuracy  
- Escalation speed  
- Communication gaps  
- Policy effectiveness vs reality  

> Red Teams do not focus on CVE counts.

---

## Key Objectives of Red Teams

### Human Security Testing
- Phishing susceptibility  
- Verification discipline  
- Reporting behavior  

---

### Physical Security Validation
- Access controls  
- Visitor handling  
- Guard response  

---

### Control Effectiveness
- Are controls enforced or just documented?  
- Are security assumptions valid?  

---

### Incident Response Readiness
- Can teams detect and respond under pressure?  
- Are playbooks usable in practice?  

---

### Supply Chain Exposure
- Trust relationships  
- Vendor access paths  

---

### Security Investment Guidance
- Identify high-impact gaps  
- Prioritize remediation realistically  

---

## Red Team vs Other Testing

| Activity            | Focus            | Duration | Visibility   |
|---------------------|------------------|----------|--------------|
| Vulnerability Scan  | Known issues     | Short    | Obvious      |
| Penetration Test    | Exploitation     | Short    | Semi-visible |
| Red Team            | Adversary goals  | Long     | Covert       |

---

## Value to Blue & Purple Teams

- Provides realistic attacker TTPs  
- Improves detection logic  
- Refines playbooks  
- Drives Purple Team collaboration  
- Reduces false confidence  

> **Blue Team takeaway:**  
> Red Teams show how attacks actually unfold, not how we hope they do.

---

## Governance & Ethics

- Always authorized  
- Clearly scoped  
- Safety controls in place  
- Findings used for improvement, not blame
