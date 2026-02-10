# Internet of Things (IoT) Security

## What IoT Security Is

IoT Security focuses on protecting:
- Internet-connected devices (sensors, cameras, wearables, appliances, industrial controllers)  
- The data they generate  
- The networks and platforms they connect to  

**Why it matters:**
- IoT devices are pervasive, always-on, and often poorly secured  
- A single compromised device can become a pivot point into larger networks  

> **Key reality:**  
> IoT devices expand the attack surface faster than traditional IT assets.

---

## Why IoT Is High Risk

IoT devices differ from traditional systems because they:
- Have limited CPU, memory, and storage  
- Often run embedded or outdated operating systems  
- Rarely receive timely security updates  
- Are deployed at scale and in diverse locations  
- Are frequently overlooked in asset inventories  

**Impact of compromise:**
- Entry point into corporate networks  
- Data theft or espionage  
- Service disruption  
- Physical damage or safety risks (industrial/medical IoT)  

---

## Common IoT Threats

- Default or hardcoded credentials  
- Weak or missing authentication  
- Insecure communication (no encryption)  
- Unpatched firmware  
- Insecure APIs and management interfaces  
- Lateral movement from IoT to IT networks  

> **SOC insight:**  
> IoT attacks often look like “noise” until correlated properly.

---

## Core Objectives of IoT Security

- Prevent unauthorized device access  
- Protect data confidentiality and integrity  
- Limit blast radius if a device is compromised  
- Maintain operational availability and safety  

---

## Key Pillars of IoT Security

### 1. Device Security
**Focus:** Secure the device itself

**Controls:**
- Disable default credentials  
- Strong authentication where supported  
- Secure boot and firmware integrity  
- Regular firmware updates  
- Minimal services enabled  

**Common failure:**  
Devices are deployed and never updated again.

---

### 2. Network Segmentation (Critical)
**Focus:** Contain compromise

**Best practices:**
- Isolate IoT devices from:
  - Corporate IT networks  
  - Sensitive systems  
- Use:
  - VLANs  
  - Firewall rules  
  - Micro-segmentation  

> **Blue-team takeaway:**  
> Segmentation is often the most effective control for weak IoT devices.

---

### 3. Secure Communication
**Focus:** Protect data in transit

**Controls:**
- Encrypted protocols where supported  
- Secure device-to-cloud communication  
- Restricted outbound traffic destinations  

**Detection value:**  
Unexpected outbound traffic is a strong compromise signal.

---

### 4. Identity & Access Management (IoT Context)
- Device identity management  
- Certificate-based authentication (preferred)  
- Role separation for management interfaces  

**Common gap:**  
Shared credentials across large fleets of devices.

---

### 5. Monitoring & Visibility
**Focus:** Detect abnormal behavior

Includes:
- Network traffic monitoring  
- Device behavior baselining  
- Alerting on anomalies  

**SOC challenge:**  
- IoT logs are often limited or nonexistent  
- Network telemetry becomes the primary detection source  

---

## Roles & Responsibilities (Shared Model)

**Information Security Team**
- Define IoT security strategy  
- Perform risk assessments and governance  
- Coordinate incident response  

**Device Manufacturers**
- Secure-by-design hardware and firmware  
- Minimize attack surface  
- Provide timely security updates  

> **Risk:**  
> Many devices are shipped insecure by default.

**Network Administrators**
- Secure IoT network segments  
- Enforce isolation and monitoring  
- Detect suspicious device behavior  

**Application Developers**
- Secure applications and APIs interacting with IoT  
- Implement authentication, authorization, and encryption  

---

## Real-World Risk Pattern

IoT breaches often follow this path:
1. Weakly secured IoT device is compromised  
2. Device used as an initial foothold  
3. Lateral movement into the corporate network  
4. Data theft or service disruption  

> **Key lesson:**  
> “Low-value” devices can lead to high-impact breaches.

---

## IoT Security Challenges

- Device diversity and scale  
- Long device lifecycles  
- Limited patching capability  
- Vendor dependency  
- Lack of centralized management
