# Module 3 – INTRODUCTION TO NETWORKING  
## 3.18 Key Exchange Mechanisms (DH, RSA, ECDH, ECDSA, IKE – CDSA-Focused Notes)

Encryption is useless if the key exchange is broken.

Key exchange mechanisms allow two parties to:
- Agree on a shared secret  
- Over an insecure channel  
- Without revealing the key to attackers  

This is foundational to:
- TLS (HTTPS)  
- VPNs (IPsec/IKE)  
- SSH  
- Secure email  
- Secure messaging  

---

## 1. Why Key Exchange Matters

If two parties want encrypted communication:
1. They need a shared key.  
2. They cannot send the key in plaintext.  
3. They must securely derive it.  

This is the core problem key exchange solves.

---

## 2. Diffie–Hellman (DH)

Diffie–Hellman allows two parties to:
- Generate a shared secret  
- Without prior shared secrets  
- Without sending the secret itself  

It relies on:
- Modular exponentiation  
- Difficulty of the discrete logarithm problem  

### Key Property

Even if an attacker sees:
- Public parameters  
- Public values exchanged  

They still cannot compute the shared secret (if parameters are strong).

### Weakness: MITM Vulnerability

Classic DH does **not authenticate** the parties.

An attacker can:
1. Intercept the exchange  
2. Establish two separate shared secrets  
3. Relay messages between both parties  

This enables a Man-in-the-Middle (MITM) attack.

**Mitigation:**  
DH must be combined with authentication (e.g., certificates, digital signatures).

### Performance

Classic finite-field DH:
- Secure with strong parameters  
- Slower compared to ECDH  

---

## 3. RSA

RSA is a public-key cryptosystem based on:
- Large prime multiplication  
- Difficulty of integer factorization  

Used for:
- Encryption  
- Digital signatures  
- Authentication  
- TLS key exchange (legacy)  
- PKI systems  

### Security Depends On:
- Key size (2048-bit minimum recommended; 3072+ for higher security)  
- Proper padding (e.g., OAEP)  

RSA is computationally heavier than elliptic-curve cryptography at comparable security levels.

---

## 4. Elliptic Curve Diffie–Hellman (ECDH)

ECDH = Diffie–Hellman using elliptic curves.

**Advantages:**
- Faster  
- Smaller key sizes  
- Stronger security per bit  
- Efficient on low-power devices  

Widely used in:
- TLS 1.2 / 1.3  
- IKE  
- Modern VPNs  
- Mobile devices  

### Forward Secrecy

When used ephemerally (ECDHE):
- Compromise of long-term private key  
- Does **not** expose past sessions  

Forward secrecy is critical in modern cryptography.

---

## 5. ECDSA (Elliptic Curve Digital Signature Algorithm)

ECDSA:
- Used for digital signatures  
- Provides authentication  
- Ensures data integrity  

Used in:
- TLS certificates  
- SSH host keys  
- Code signing  
- Blockchain systems  

---

## 6. Algorithm Comparison

| Algorithm | Purpose            | Strength                     |
|-----------|--------------------|------------------------------|
| DH        | Key exchange       | Secure with strong params    |
| RSA       | Encryption/signing | Secure with large keys       |
| ECDH      | Key exchange       | Faster & more efficient      |
| ECDSA     | Digital signatures | Efficient & strong           |

**Modern best practice:**  
ECDHE + AES + SHA-2 / SHA-3

---

## 7. Internet Key Exchange (IKE)

IKE is used in:
- IPsec VPNs  
- Site-to-site VPN  
- Remote access VPN  

IKE negotiates:
- Encryption algorithms  
- Authentication methods  
- Diffie–Hellman groups  
- Shared keys  

Runs on:UDP 500

---

## 8. IKE Modes

### Main Mode
- 3 phases  
- Identity protection  
- More secure  
- Slightly slower  

### Aggressive Mode
- Fewer round trips  
- Faster  
- No identity protection  
- Less secure  

Aggressive mode can leak:
- Identity hashes  
- Information usable for PSK brute force  

**Security recommendation:**  
Avoid aggressive mode in production environments.

---

## 9. Pre-Shared Keys (PSK)

PSK:
- Shared secret configured manually  
- Used for authentication in IKE  

**Advantages:**
- Simple  
- Easy setup  

**Disadvantages:**
- Must be distributed securely  
- Vulnerable to brute force  
- If leaked → full compromise  

**Enterprise best practice:**  
Use certificates instead of PSKs.

---

## 10. Where These Mechanisms Are Used

| Protocol        | Key Exchange Used |
|-----------------|-------------------|
| TLS             | ECDHE / RSA       |
| IPsec           | DH / ECDH         |
| SSH             | DH / ECDH         |
| Kerberos PKINIT | RSA               |
| VPN (IKE)       | DH / ECDH         |

---

## 11. Defensive Considerations

Security depends on:
- Strong DH groups  
- Strong elliptic curves  
- Large RSA key sizes  
- Proper certificate validation  
- Avoiding weak modes (IKE aggressive)  

**Common weaknesses:**
- Weak DH groups (e.g., 1024-bit)  
- Reused PSKs  
- No forward secrecy  
- Self-signed certificates without validation  
- Weak padding in RSA implementations  

---

## CDSA-Level Interview Questions

1. What problem does Diffie–Hellman solve?  
2. Why is classic DH vulnerable to MITM?  
3. What is forward secrecy?  
4. Difference between RSA and ECDH?  
5. Why is ECDH preferred over DH?  
6. Difference between IKE main and aggressive mode?  
7. Why is PSK risky?
