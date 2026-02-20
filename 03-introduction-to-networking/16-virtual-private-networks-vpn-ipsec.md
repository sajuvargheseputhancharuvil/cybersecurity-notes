# Module 3 – INTRODUCTION TO NETWORKING  
## 3.16 Virtual Private Networks (VPN & IPsec – CDSA-Focused Notes)

A VPN extends a private network across a public network (usually the Internet) by creating an encrypted tunnel between a client and a remote network.

From a defensive perspective, a VPN:
- Expands the internal network boundary  
- Bypasses perimeter restrictions  
- Introduces remote attack surface  
- Becomes a high-value authentication target  

If compromised, a VPN can give attackers internal access.

---

## 1. What a VPN Actually Does

A VPN:
- Authenticates the user/device  
- Establishes an encrypted tunnel  
- Assigns an internal IP address  
- Routes traffic as if the device were local  

**Example:**

An administrator at home connects to the VPN →  
Receives internal IP →  
Accesses internal servers →  
All traffic encrypted over the Internet.

---

## 2. Why Organizations Use VPNs

### Secure Remote Access
Employees can:
- Work from home  
- Travel  
- Manage internal services  

### Encryption
Traffic is encrypted, protecting:
- Credentials  
- Internal services  
- Sensitive business data  

### Cost-Effective
Uses public Internet instead of:
- Leased lines  
- Dedicated private circuits  

### Site-to-Site Connectivity
Connect:
- Branch offices  
- Remote data centers  
- Hybrid cloud networks  

---

## 3. Core VPN Components

| Component       | Role                         |
|-----------------|------------------------------|
| VPN Client      | Installed on remote device   |
| VPN Server      | Accepts connections          |
| Encryption      | Protects tunnel traffic      |
| Authentication  | Verifies identity            |

Authentication methods include:
- Pre-shared key (PSK)  
- Certificates  
- Username/password  
- MFA  

---

## 4. Common VPN Ports & Protocols

| Protocol        | Port / Protocol Number |
|-----------------|-------------------------|
| PPTP            | TCP 1723                |
| IKEv1 / IKEv2   | UDP 500                 |
| IPsec NAT-T     | UDP 4500                |
| ESP             | IP Protocol 50          |
| AH              | IP Protocol 51          |

**Important:**

ESP and AH are not TCP/UDP ports.  
They are separate IP protocol numbers.

---

## 5. IPsec – Enterprise-Grade VPN

IPsec operates at Layer 3 (Network Layer).

It provides:
- Encryption  
- Integrity  
- Authentication  

### IPsec Protocols

**Authentication Header (AH)**
- Integrity + authenticity  
- No encryption  
- Rarely used alone  

**Encapsulating Security Payload (ESP)**
- Encryption  
- Optional integrity  
- Most common in real-world deployments  

---

## 6. IPsec Modes

### Transport Mode
- Encrypts payload only  
- IP header remains visible  
- Used for host-to-host  

### Tunnel Mode
- Encrypts entire packet  
- Original IP header hidden  
- Used for site-to-site VPN  

Tunnel mode = true VPN tunneling.

---

## 7. IKE (Internet Key Exchange)

IKE:
- Negotiates encryption algorithms  
- Establishes shared keys  
- Uses Diffie-Hellman  
- Runs on UDP 500  

Without IKE, IPsec cannot securely establish keys.

---

## 8. Firewall Requirements for IPsec

To allow IPsec VPN through a firewall:
- UDP 500 (IKE)  
- UDP 4500 (NAT-T)  
- IP Protocol 50 (ESP)  
- IP Protocol 51 (AH)  

Blocking any of these breaks tunnel setup.

---

## 9. PPTP (Legacy – Insecure)

PPTP:
- Uses TCP 1723  
- Based on PPP  
- Uses MSCHAPv2 authentication  
- Uses weak DES-based encryption  

**Major problem:**  
MSCHAPv2 can be cracked quickly with modern hardware.

PPTP is deprecated and should not be used.

---

## 10. Secure Alternatives to PPTP

- L2TP/IPsec  
- IKEv2/IPsec  
- OpenVPN  
- WireGuard  
- SSL VPNs  

---

## 11. VPN Security Risks

VPNs introduce serious risks if misconfigured:

### Weak Authentication
- Password-only VPN  
- No MFA  
- Reused credentials  

### Split-Tunnel Risks
Split-tunnel allows:
- Internet traffic outside VPN  
- Malware bypassing inspection  

### Credential Stuffing
VPN portals are often targeted in:
- Brute-force attacks  
- Password spraying  

### Misconfigured IPsec
Weak:
- Diffie-Hellman groups  
- Encryption algorithms  
- Lifetime settings  

---

## 12. Defensive Monitoring Checklist

Monitor:
- Failed VPN logins  
- Logins from unusual geolocation  
- Logins outside work hours  
- Multiple sessions from same account  
- Abnormal bandwidth spikes  
- VPN access followed by lateral movement  

VPN logs are critical in breach investigations.

---

## 13. CDSA-Level Attack Scenarios

Common VPN abuse patterns:
1. Stolen credentials → VPN login  
2. VPN login → Internal reconnaissance  
3. SMB/RDP movement  
4. Privilege escalation  
5. Data exfiltration via VPN tunnel  

VPN becomes attacker’s stealth entry point.

---

## 14. Interview Questions You Should Handle

1. Difference between Transport and Tunnel mode?  
2. What does ESP provide?  
3. Why is PPTP insecure?  
4. What port does IKE use?  
5. What is NAT-T?  
6. Why is MFA important for VPN?  
7. What is split-tunneling risk?  
