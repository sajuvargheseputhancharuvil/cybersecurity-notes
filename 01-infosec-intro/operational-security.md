# Operational Security (OpSec)

## What Operational Security Is

Operational Security (OpSec) focuses on protecting information and systems during day-to-day operations.

Unlike Network or Application Security (which focus on technical layers), OpSec focuses on:
- Processes  
- People  
- Operational decisions  
- How information is handled in real-world workflows  

**Primary goal:**
Ensure sensitive information remains:
- Confidential  
- Accurate  
- Available  

and prevent accidental exposure, misuse, or abuse during routine operations.

---

## Why OpSec Matters

Most security incidents are not caused by advanced exploits. They are caused by:
- Poor access management  
- Human error  
- Weak operational processes  
- Misconfigurations  
- Lack of monitoring  

> **Key point:**  
> OpSec is where policy meets reality.

---

## Core OpSec Process (Lifecycle View)

Operational Security follows a continuous, repeatable cycle.

### 1. Asset Identification
Identify what needs protection, including:
- Sensitive data  
- Systems  
- Credentials  
- Infrastructure  
- Physical assets  

**Why this matters:**
- You cannot protect what you do not know exists  
- Asset value determines the level of protection  

---

### 2. Threat Identification
Understand what could go wrong.

**Common threats:**
- Insider misuse  
- Social engineering  
- Credential theft  
- Physical access abuse  
- Accidental data leakage  

> **Blue-team mindset:**  
> Assume users make mistakes — attackers exploit them.

---

### 3. Vulnerability Identification
Identify weaknesses in operations.

**Common OpSec vulnerabilities:**
- Excessive permissions  
- Shared accounts  
- Weak password policies  
- Poor offboarding processes  
- Insecure physical access  

> **Key idea:**  
> Many vulnerabilities are process failures, not software bugs.

---

### 4. Access Control
Control who can access what, and when.

Includes:
- Authentication (identity verification)  
- Authorization (permission enforcement)  

**Best practices:**
- Least privilege  
- Role-based access  
- MFA for sensitive systems  
- Regular access reviews  

> **Critical OpSec failure:**  
> Access not revoked after role changes or employee exit.

---

### 5. Monitoring
Continuously observe operations.

Includes:
- User activity monitoring  
- Access logs  
- System changes  
- Policy violations  

**SOC relevance:**  
OpSec failures often surface as:
- Unusual login patterns  
- Privilege misuse  
- Policy violations  

---

## Key Components of Operational Security

### Access Management
- Central to OpSec effectiveness  
- Covers:
  - User onboarding  
  - Role changes  
  - Offboarding  
- Requires:
  - Periodic access audits  
  - Immediate revocation when needed  

---

### Asset Management
- Maintain an up-to-date inventory of:
  - Hardware  
  - Software  
  - Data  
- Enables:
  - Risk prioritization  
  - Faster incident response  

> **Missing assets = blind spots**

---

### Change Management
Controls how systems and processes are modified.

Requires:
- Approval workflows  
- Testing  
- Rollback plans  

**Why it matters:**  
Many breaches originate from:
- Poorly tested changes  
- Emergency fixes  
- Unauthorized modifications  

---

### Security Awareness Training
Humans are part of the attack surface.

**Focus areas:**
- Phishing awareness  
- Password hygiene  
- Data handling practices  

A strong OpSec culture reduces:
- Social engineering success  
- Insider incidents  

---

## Responsibility for OpSec

### Primary Ownership
- Information Security Team  
- Strategic oversight by:
  - CISO or equivalent  

### Shared Responsibility
OpSec requires coordination across:
- IT – systems and access  
- HR – onboarding/offboarding  
- Legal & Compliance – regulatory alignment  
- Management – enforcement and accountability  
- Employees – daily execution  

> **Key principle:**  
> OpSec fails if treated as “security’s problem only.”

---

## Testing Operational Security

### Why Test OpSec?
- Policies do not guarantee enforcement  
- Humans behave differently under pressure  
- Real attackers exploit operational gaps  

### How OpSec Is Tested
- Internal security assessments  
- External penetration testing  
- Social engineering simulations  
- Access control testing  
- Configuration reviews  

**Blue-team benefit:**
- Identifies gaps before real abuse  
- Improves detection and response playbooks  

---

## OpSec vs Other Security Domains

- **Network Security** → traffic and connectivity  
- **Application Security** → code and logic  
- **Operational Security** → people, process, execution  

Most real-world breaches combine failures across all three.
