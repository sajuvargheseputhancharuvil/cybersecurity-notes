# Physical Security

## What Physical Security Is

Physical Security protects tangible assets that store, process, or transmit information, including:
- Buildings and facilities  
- Servers, racks, endpoints, and network devices  
- Storage media and printed documents  

**Primary goal:**  
Prevent unauthorized physical access, theft, damage, or tampering that could compromise **Confidentiality, Integrity, and Availability (CIA)**.

> **Key reality:**  
> Strong cyber controls mean little if an attacker can physically access the hardware.

---

## Why Physical Security Matters

- Prevents data breaches via device theft or tampering  
- Protects personnel and visitors  
- Maintains operational continuity  
- Often required for regulatory compliance  
- Underpins all other security domains  

---

## Defense in Depth (Physical)

Physical security relies on layered controls to:
- **Deter** – make attacks unattractive  
- **Detect** – identify attempts quickly  
- **Delay** – slow attackers  
- **Respond** – contain and resolve  

**Typical layers:**
1. Perimeter (fencing, barriers)  
2. Entry points (doors, locks, access readers)  
3. Interior zones (segmented areas)  
4. Asset-level protections (racks, safes)  
5. Response (guards, procedures)  

---

## Core Physical Security Controls

### Access Control
- Badge readers, biometrics, PINs  
- Role-based access to zones  
- MFA for high-security areas  
- Regular access reviews and immediate revocation  

**Common failures:**
- Propped doors  
- Shared badges  
- Tailgating  

---

### Surveillance & Monitoring
- CCTV coverage (entry/exit points, sensitive zones)  
- Centralized monitoring and alerting  
- Defined retention policies for footage  

**Purpose:**  
Detection, deterrence, and post-incident investigation.

---

### Physical Barriers
- Reinforced doors and locks  
- Mantraps for sensitive areas  
- Secured racks and cages  

**Goal:**  
Delay intruders long enough for response.

---

### Environmental Controls
- Fire suppression  
- Temperature and humidity controls  
- Power redundancy (UPS, generators)  

**Impact:**  
Protects availability and equipment integrity.

---

### Visitor Management
- Identity verification  
- Badging and escorting  
- Visitor logs and access limits  

**Common gap:**  
Unescorted visitors in secure areas.

---

### Personnel Security
- Clear desk / screen policies  
- Awareness training (tailgating, badge use)  
- Consistent enforcement of procedures  

---

## Roles & Responsibilities

### Ownership
- Physical Security Team (often under CSO or CISO)  
- Close coordination with:
  - Facilities Management  
  - IT / Security Operations  
  - HR (onboarding/offboarding)  

### Shared Responsibility
All employees must:
- Follow access rules  
- Report anomalies  
- Protect credentials and badges  

> **Key principle:**  
> Physical security fails fastest through human shortcuts.

---

## Physical Security Testing (Red Team / Assessments)

### Why Test
- Policies ≠ enforcement  
- Humans are exploitable  
- Physical gaps can bypass cyber defenses  

### What’s Tested
- Access controls and tailgating  
- Lock quality and door integrity  
- Perimeter coverage and lighting  
- Camera placement and blind spots  
- Guard response times  
- Visitor handling procedures  
- Protection of IT closets and racks  
- Unattended workstations  

### Common Physical Vulnerabilities
- Unsecured access points  
- Weak or outdated locks  
- Poor key/badge management  
- Insufficient lighting  
- Exposed IT infrastructure  
- Weak visitor protocols  
- Unlocked or unattended devices  

**Testing methods may include:**
- Authorized entry attempts  
- Social engineering  
- After-hours access checks  
- Response and escalation drills  

---

## Physical Security & InfoSec (Big Picture)

Physical access can:
- Bypass authentication  
- Enable data exfiltration  
- Destroy evidence  
- Disrupt availability  

Physical security must be integrated with:
- Network Security  
- Application Security  
- Operational Security  
- Disaster Recovery & Business Continuity (DR/BC)  
