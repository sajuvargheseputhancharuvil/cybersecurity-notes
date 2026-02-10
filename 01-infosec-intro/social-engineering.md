# Social Engineering

## What Social Engineering Is

Social Engineering is an attack technique that manipulates **people**, not systems, to gain unauthorized access, information, or actions.

**Key characteristic:**
- Exploits human psychology (trust, fear, urgency, curiosity, authority)

**Why it’s dangerous:**
- Bypasses technical controls  
- Targets the human element, often the weakest link in security  

**Core security principles affected:**
- Confidentiality  
- Integrity  
- Availability (indirectly, via follow-on attacks)

---

## Why Social Engineering Works

Humans are conditioned to:
- Be helpful  
- Trust authority  
- Act quickly under pressure  

Attackers exploit this by:
- Imitating trusted identities  
- Creating believable scenarios  
- Abusing routine business processes  

> **Key reality:**  
> One manipulated user can nullify multiple security layers.

---

## Common Social Engineering Techniques

### 1. Phishing
**Most common technique**

- Deceptive emails, messages, or links  
- Masquerade as:
  - Banks  
  - IT support  
  - Cloud services  

**Goals:**
- Steal credentials  
- Deliver malware  
- Redirect users to fake sites  

**Variants:**
- Spear phishing (targeted)  
- Whaling (executives)  
- Smishing (SMS)  
- Vishing (voice)  

**SOC relevance:**  
Primary initial access vector for ransomware and APTs.

---

### 2. Pretexting
- Attacker invents a fake scenario (pretext)  
- Pretends to be:
  - IT staff  
  - Vendors  
  - Auditors  

**Common abuses:**
- Password resets  
- MFA fatigue  
- Identity verification bypass  

---

### 3. Baiting
- Exploits curiosity or greed  
- Examples:
  - Infected USB drives  
  - “Free” downloads  

> **Blue-team insight:**  
> Baiting often bridges physical and cyber security gaps.

---

### 4. Tailgating (Piggybacking)
- Physical social engineering  
- Attacker follows an authorized person into a secure area  

**Why it works:**
- Politeness  
- Social pressure  
- Lack of enforcement  

**Impact:**  
Physical access can lead directly to system compromise.

---

### 5. Quid Pro Quo
- “Something for something”  
- Offers a benefit in exchange for:
  - Credentials  
  - Access  
  - Actions  

**Examples:**
- Fake tech support  
- Promised upgrades or fixes  

---

## Impact of Social Engineering

### Data Breaches
- Credential theft  
- Unauthorized system access  

### Financial Loss
- Fraud  
- Ransomware  
- Recovery costs  

### Reputational Damage
- Loss of trust  
- Long-term brand impact  

### Operational Disruption
- Malware infections  
- Account lockouts  
- Service downtime  

> **Why impact is severe:**  
> Social engineering often enables larger, more damaging attacks.

---

## Detection (SOC Perspective)

**Indicators may include:**
- Unusual login behavior after user interaction  
- MFA fatigue patterns  
- Access outside normal hours  
- Credential use from new locations/devices  
- Sudden privilege changes  

**Key telemetry:**
- Authentication logs  
- Email security alerts  
- Endpoint events  
- User reports (critical signal)

---

## Prevention & Mitigation

### Security Awareness Training
- Regular, realistic training  
- Focus on:
  - Phishing recognition  
  - Verification habits  
  - Reporting procedures  

> **Reality:**  
> Training reduces risk — it does not eliminate it.

---

### Technical Controls
- Email filtering  
- MFA (with abuse protections)  
- Least privilege  
- Conditional access  
- USB restrictions  

---

### Process Controls
- Verification procedures for sensitive requests  
- No credential sharing — ever  
- Clear escalation paths  

---

### Culture Matters
- Encourage reporting without blame  
- Fast reporting limits damage  
- Silence helps attackers  

---

## Role of Red Team & Testing

- Phishing simulations  
- Physical access tests  
- Social engineering assessments  

**Measures:**
- Human resilience  
- Process effectiveness  

**Blue-team benefit:**
- Improves detection  
- Refines response playbooks  
- Identifies high-risk workflows
