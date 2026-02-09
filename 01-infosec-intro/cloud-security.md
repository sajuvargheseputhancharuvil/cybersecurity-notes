# Cloud Security

## What Cloud Security Is

Cloud Security focuses on protecting:
- Data  
- Applications  
- Workloads  
- Identities  

that run in cloud environments.

**Key challenge:**
- Cloud environments are shared, dynamic, and highly exposed  
- Security failures are usually caused by **misconfiguration**, not cloud provider failure  

---

## Why Cloud Security Is Different

Compared to on-prem environments, the cloud introduces:
- Shared infrastructure  
- Rapid scalability  
- Public exposure by default  
- Heavy reliance on identity  

> **Key defensive mindset:**  
> In the cloud, **identity is the new perimeter**.

---

## Shared Responsibility Model (Exam-Critical)

Security responsibilities are split between the cloud provider and the customer.

### Cloud Service Provider (CSP)
**Responsible for:**
- Physical data centers  
- Underlying infrastructure  
- Core cloud services  

**Examples:**
- Hardware  
- Physical access  
- Hypervisors (depending on service model)  

---

### Customer / Organization
**Responsible for:**
- Data protection  
- Identity and access management  
- Secure configuration of services  
- Application security  
- Monitoring and logging  

> **Reality:**  
> Most cloud breaches occur because customers misunderstand or neglect their responsibilities.

---

## Common Cloud Threats

- Misconfigured storage (publicly exposed buckets)  
- Insecure APIs  
- Poor authentication or authorization  
- Account hijacking (stolen credentials or tokens)  
- Over-privileged identities  
- Insufficient logging and delayed detection  

---

## Key Areas of Cloud Security

### 1. Data Protection
- Encrypt data:
  - At rest  
  - In transit  
- Manage encryption keys securely  
- Classify sensitive data  

**Goal:**  
Limit impact even if access is compromised.

---

### 2. Identity & Access Management (IAM)
IAM is the central pillar of cloud security.

Controls:
- Who can access what  
- From where  
- Under which conditions  

**Best practices:**
- Least privilege  
- Role-based access  
- MFA everywhere  
- Regular access reviews  

> **SOC reality:**  
> Most cloud incidents begin with stolen or abused credentials.

---

### 3. Cloud Network Security
- Virtual firewalls  
- Network segmentation  
- VPNs / private connectivity  
- Secure ingress and egress controls  

**Important shift:**  
Network security still matters, but identity enforcement is stronger in cloud environments.

---

### 4. Compliance & Governance
- Enforce security standards  
- Meet regulatory requirements  
- Continuous compliance monitoring  

Includes:
- Logging requirements  
- Data residency controls  
- Audit readiness  

---

## Cloud Security Operations

### Continuous Monitoring
- Cloud activity logs  
- Identity events  
- Configuration changes  

**SOC focus:**
- Detect misconfigurations  
- Identify privilege abuse  
- Monitor suspicious API activity  

---

### Patch & Configuration Management
- Cloud services evolve rapidly  
- Default settings are often insecure  
- Continuous review is mandatory  

---

### Security Awareness
- Administrative mistakes are high-impact  
- Training reduces:
  - Accidental exposure  
  - Credential misuse  

---

## Responsibility & Governance

**Cloud Provider**
- Secures the platform  
- Guarantees infrastructure availability  

**Customer / Admin**
- Secures:
  - Data  
  - Identities  
  - Configurations  
  - Applications  

**Security Teams**
- Define cloud security strategy  
- Perform risk assessments  
- Monitor cloud environments  
- Coordinate incident response  

---

## Testing Cloud Security

### Why Testing Is Critical
- Cloud environments change rapidly  
- Manual reviews do not scale  
- Attackers exploit configuration drift  

### How Cloud Security Is Tested
- Cloud penetration testing  
- IAM permission reviews  
- Configuration audits  
- Simulated account compromise  

**Pen-testing outcomes:**
- Validate real attack paths  
- Improve detection logic  
- Harden configurations
