# Module 3 – INTRODUCTION TO NETWORKING  
## 3.19 Authentication Protocols (Kerberos, TLS, EAP, SAML, MFA – CDSA-Focused Notes)

Authentication answers one critical question:

> “Are you really who you claim to be?”

Without authentication:
- Encryption is useless  
- Authorization is meaningless  
- Network access control collapses  

This section focuses on how identity is verified in enterprise networks and what defenders must understand.

---

## 1. Authentication vs Authorization (Important Distinction)

- **Authentication** → Verifies identity  
- **Authorization** → Determines access rights  

Example:
- Kerberos authenticates a user  
- ACL or RBAC decides what they can access  

Many protocols mix both concepts (e.g., SAML, OAuth/OIDC).

---

## 2. Kerberos

Kerberos is a ticket-based authentication protocol used in:
- Active Directory environments  
- Enterprise Windows domains  
- Many Linux enterprise setups  

It uses a **Key Distribution Center (KDC)**.

### How Kerberos Works (Simplified)

1. User authenticates to KDC  
2. KDC issues a Ticket Granting Ticket (TGT)  
3. User requests a service ticket  
4. Service ticket is used to access a resource  

No passwords are sent over the network after the initial authentication.

### Security Considerations

Common attacks:
- Kerberoasting  
- AS-REP roasting  
- Golden Ticket  
- Silver Ticket  
- Pass-the-Ticket  

Kerberos security depends heavily on:
- Strong service account passwords  
- Proper time synchronization  
- Domain Controller hardening  

---

## 3. TLS / SSL

SSL is deprecated and replaced by TLS.

TLS provides:
- Encryption  
- Integrity  
- Authentication (via certificates)  

Used in:
- HTTPS  
- Secure email  
- VPNs  
- APIs  
- Secure application traffic  

### Authentication in TLS

TLS uses:
- Digital certificates  
- Public Key Infrastructure (PKI)  

Clients verify:
- Server certificate  
- CA trust chain  
- Validity period  
- Domain name  

If certificate validation fails, MITM attacks become possible.

---

## 4. OAuth (Authorization Framework)

Important distinction:

OAuth is an **authorization framework**, not an authentication protocol.

It allows:
- Third-party app access  
- Without sharing user passwords  

Example:
- “Login with Google”  

OAuth tokens grant limited access to resources.

---

## 5. OpenID & OpenID Connect (OIDC)

- **OpenID**  
  - Decentralized authentication protocol  
  - Single identity across multiple services  

- **OpenID Connect (OIDC)**  
  - Built on OAuth  
  - Adds authentication layer  

Modern web SSO commonly uses OAuth + OIDC.

---

## 6. SAML

**Security Assertion Markup Language (SAML)** is widely used for:
- Enterprise Single Sign-On (SSO)  
- Cloud services  
- Identity federation (AD ↔ SaaS)  

It exchanges:
- XML-based authentication assertions  

Common in:
- Corporate VPN portals  
- Office 365 / SaaS integration  
- Enterprise identity federation  

---

## 7. MFA & 2FA

Multi-Factor Authentication combines:

1. Something you know (password)  
2. Something you have (token, phone)  
3. Something you are (biometric)  

- **2FA** = two factors  
- **MFA** = two or more factors  

MFA drastically reduces the risk of password-based compromise.

---

## 8. FIDO / FIDO2

FIDO Alliance standards enable:
- Passwordless authentication  
- Hardware-based authentication  
- Public-key cryptography  

Used in:
- Security keys (USB/NFC)  
- Windows Hello  
- Modern passwordless login systems  

Highly resistant to phishing attacks.

---

## 9. PKI (Public Key Infrastructure)

PKI provides:
- Certificate issuance  
- Trust chains  
- Certificate revocation  
- Identity verification  

Core components:
- Certificate Authority (CA)  
- Registration Authority (RA)  
- Certificate Revocation List (CRL)  

Used in:
- TLS  
- VPNs  
- Smart cards  
- Email encryption  

---

## 10. PAP vs CHAP

### PAP (Password Authentication Protocol)
- Sends passwords in cleartext  
- Extremely insecure  
- Obsolete  

### CHAP (Challenge Handshake Authentication Protocol)
- Uses challenge-response  
- Password never sent directly  
- Hash-based verification  

More secure than PAP, but outdated compared to modern authentication mechanisms.

---

## 11. EAP (Extensible Authentication Protocol)

EAP is a **framework**, not a single protocol.

Used in:
- 802.1X  
- Enterprise WiFi  
- VPN authentication  

### Common EAP Types

| EAP Type  | Security Level |
|----------|----------------|
| LEAP     | Weak           |
| PEAP     | Moderate       |
| EAP-TLS  | Strong         |
| EAP-TTLS | Strong         |

---

## 12. LEAP vs PEAP vs EAP-TLS

### LEAP (Deprecated)
- Cisco proprietary  
- RC4-based  
- Vulnerable to dictionary attacks  

### PEAP
- TLS tunnel  
- Protects inner authentication (e.g., MSCHAPv2)  
- Server certificate validation required  

### EAP-TLS (Recommended)
- Mutual certificate-based authentication  
- No password-based auth  
- Strongest enterprise wireless authentication method  
- Requires PKI  

---

## 13. SSH

Secure remote access protocol.

Provides:
- Encrypted communication  
- Authentication via:
  - Passwords  
  - Public keys  
  - Certificates  

Public key authentication is significantly more secure than passwords.

---

## 14. HTTPS

HTTP over TLS.

Provides:
- Encryption  
- Server authentication  
- Optional client authentication  

Security depends entirely on:
- TLS configuration  
- Certificate validation  

---

## 15. SSO (Single Sign-On)

Allows:
- One authentication  
- Access to multiple services  

Common in:
- Enterprise environments  
- Cloud platforms  

Implemented using:
- SAML  
- OAuth / OIDC  
- Kerberos  

---

## Defensive Observations

Common authentication weaknesses:
- Weak passwords  
- No MFA  
- Self-signed certificates in production  
- Disabled certificate validation  
- Reused PSKs  
- Legacy protocols (PAP, LEAP)  
- Poor Kerberos hardening  

---

## Protocol Usage Context

| Scenario                   | Protocol            |
|---------------------------|---------------------|
| Windows domain login      | Kerberos            |
| Web login                 | HTTPS + OAuth/OIDC  |
| Enterprise WiFi           | EAP-TLS             |
| VPN authentication        | IKE + Certificates  |
| Remote server management  | SSH                 |
| Enterprise SSO            | SAML                |

---

## CDSA-Level Interview Questions

1. Difference between authentication and authorization?  
2. Why is Kerberos more secure than NTLM?  
3. What is Kerberoasting?  
4. Why is LEAP insecure?  
5. Why is EAP-TLS preferred?  
6. Why is MFA important?  
7. What is certificate validation?  
8. How does TLS authenticate a server?
