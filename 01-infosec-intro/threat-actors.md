# Threat Actors

## What a Threat Actor Is

A Threat Actor is an individual or organized group that conducts cyber attacks against systems, networks, or data.

**Key distinction:**
- **Blue Team** → defends systems  
- **Red Team** → simulates attackers to improve defense  
- **Threat Actors** → conduct real attacks with malicious intent  

Threat actors may be:
- Highly organized teams  
- Small groups  
- Solo individuals (“lone wolves”)  

---

## Threat Actor Teams (How They’re Structured)

Well-resourced threat actors operate as specialized teams rather than generalists.

**Common roles inside a threat actor team:**
- **Malware / Tool Developers**  
  - Create custom malware, exploits, loaders  
- **Network Specialists**  
  - Identify network weaknesses and pivot paths  
- **Social Engineers**  
  - Exploit human behavior (phishing, pretexting)  
- **Data Analysts**  
  - Process stolen data (credentials, IP, intelligence)  
- **Operators**  
  - Execute intrusions, lateral movement, exfiltration  
- **Team Leaders / Strategists**  
  - Set objectives, coordinate phases, manage risk  

> **Key insight:**  
> Mature threat actors mirror legitimate IT and security teams — with opposite goals.

---

## Solo Threat Actors (Lone Wolves)

- Operate independently  
- Motivated by:
  - Financial gain  
  - Ideology  
  - Curiosity or revenge  
- Capabilities vary widely:
  - From basic phishing  
  - To advanced malware development  

**Detection challenge:**
- Unpredictable tactics  
- Smaller footprint, but sometimes less disciplined  

---

## How Threat Actors Operate (Common Traits)

### Low-and-Slow Approach
- Avoid noisy techniques (e.g., brute force)  
- Blend into normal activity  
- Extend dwell time  

### Tool Choice
- Prefer:
  - Living-off-the-land tools  
  - Legitimate administrative utilities  
- Avoid:
  - Easily detectable malware  
  - Obvious indicators  

### Operational Discipline
- Careful timing  
- Minimal footprint  
- Redundant access paths  

> **SOC takeaway:**  
> Silence and patience often indicate skill, not absence of threat.

---

## Threat Actor Objectives

### 1. Financial Gain
- Ransomware  
- Fraud  
- Data theft for resale  
- Cryptomining abuse  

---

### 2. Espionage
- Government intelligence  
- Corporate secrets  
- Research & development  
- Supply chain insight  

> Often long-term and stealthy.

---

### 3. Disruption
- Service outages  
- Data destruction  
- Infrastructure sabotage  
- Psychological or economic impact  

---

### 4. Ideological / Hacktivism
- Political, religious, or social motives  
- Symbolic targets  
- Focus on publicity and impact  

---

### 5. Revenge
- Former employees  
- Disgruntled partners  
- Personal grievances  

> Often overlaps with insider threat.

---

## Threat Actor Capability Levels (Analyst View)

- **Low:** Script kiddies, basic phishing, reused malware  
- **Medium:** Organized cybercrime, ransomware groups  
- **High:** APTs, state-sponsored groups, supply-chain attackers  

> **Important:**  
> Motivation does not equal capability — assess both.

---

## Detection & Defense Implications (SOC Perspective)

**What to watch for:**
- Credential abuse  
- Unusual access patterns  
- Lateral movement  
- Data staging and exfiltration  
- Long dwell time with minimal alerts  

**Why attribution is hard:**
- Shared tools  
- False flags  
- Infrastructure reuse  
- Overlapping TTPs  

> **Focus on:**  
> Behavior and impact, not actor names.

---

## Relationship to Red, Blue, and Purple Teams

- Threat actors define real-world tactics  
- Red Teams emulate threat actors to test defenses  
- Blue Teams detect and respond  
- Purple Teams close gaps through collaboration
