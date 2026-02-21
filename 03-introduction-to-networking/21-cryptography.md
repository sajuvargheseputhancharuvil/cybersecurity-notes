# 3.21 Cryptography (Symmetric, Asymmetric, AES, Modes – CDSA-Focused Notes)

Cryptography is the foundation of:
- HTTPS  
- VPNs  
- SSH  
- WiFi security  
- Email encryption  
- Cloud security  

If cryptography fails, everything above it fails.

This section focuses on how encryption works, where it’s used, and where it fails in practice.

---

## 1. Core Cryptography Concepts

Encryption transforms:

Plaintext → Ciphertext

Using:
- Algorithms  
- Keys  
- Mathematical operations  

There are two primary categories:
1. Symmetric encryption  
2. Asymmetric encryption  

They are almost always used together in modern protocols.

---

## 2. Symmetric Encryption

Symmetric encryption uses:
- One shared secret key  
- The same key for encryption and decryption  

Both sender and receiver must securely share the key.

### Advantages
- Very fast  
- Efficient for large data  
- Low computational overhead  

Used for:
- Disk encryption  
- VPN tunnels  
- TLS session encryption  
- WiFi encryption  
- File encryption  

### Main Problem
Key distribution.  
If an attacker obtains the key, all encrypted data is compromised.

---

## 3. DES (Data Encryption Standard)

DES:
- 64-bit block cipher  
- 56-bit effective key  
- Symmetric encryption  

Weakness:
- 56-bit key is too small  
- Brute-force attacks are feasible  

DES is obsolete and should not be used.

---

## 4. 3DES (Triple DES)

3DES performs:
Encrypt → Decrypt → Encrypt  

More secure than DES but:
- Still based on outdated design  
- Slower performance  
- Deprecated in modern standards  

Not recommended for new systems.

---

## 5. AES (Advanced Encryption Standard)

AES replaced DES.

Key sizes:
- 128-bit  
- 192-bit  
- 256-bit  

Block size:
- 128 bits  

Advantages:
- Strong security  
- High performance  
- Hardware acceleration support  
- Efficient on modern CPUs  

### Where AES Is Used
- TLS  
- IPsec  
- SSH  
- WPA2/WPA3  
- BitLocker  
- OpenSSL  
- PGP  

AES is the industry standard symmetric cipher.

---

## 6. Asymmetric Encryption

Uses two keys:
- Public key  
- Private key  

Public key encrypts.  
Private key decrypts.

Anyone can encrypt with the public key.  
Only the private key holder can decrypt.

### Advantages
- Solves key distribution problem  
- Enables digital signatures  
- Enables authentication  
- Enables secure key exchange  

### Examples
- RSA  
- ECC (Elliptic Curve Cryptography)  
- PGP  
- TLS certificates  
- SSH key pairs  

---

## 7. Why Modern Systems Combine Both

Asymmetric encryption is computationally expensive and slow.

Modern systems use:
1. Asymmetric crypto to exchange session keys  
2. Symmetric crypto to encrypt bulk data  

Example:
TLS handshake uses RSA or ECDHE  
Session encryption uses AES  

---

## 8. Cipher Modes (Critical for Security)

Block ciphers encrypt fixed-size blocks.  
Cipher modes determine how blocks are chained together.

Incorrect mode selection can make strong encryption insecure.

### ECB (Electronic Code Book) – Insecure
- Identical plaintext blocks produce identical ciphertext blocks  
- Reveals patterns  
- Must never be used for sensitive data  

### CBC (Cipher Block Chaining)
- Each block depends on the previous block  
- More secure than ECB  
- Used in older TLS and disk encryption  

Weaknesses:
- Padding oracle attacks  
- Requires secure IV handling  

### CFB / OFB
- Stream-like modes  
- Used in real-time encryption and SSH  

### CTR (Counter Mode)
- Converts block cipher into stream cipher  
- Fast and parallelizable  
- Used in IPsec and BitLocker  

Security note:
Nonces must never be reused.

### GCM (Galois/Counter Mode) – Recommended

Provides:
- Encryption  
- Integrity (Authenticated Encryption)  

Used in:
- TLS 1.2+  
- TLS 1.3  
- VPNs  
- Wireless encryption  

GCM is an AEAD mode (Authenticated Encryption with Associated Data).

Encryption without integrity is dangerous.

---

## 9. Integrity and Authentication

Encryption alone is insufficient.

Security also requires:
- Data integrity  
- Authenticity  

Mechanisms include:
- HMAC  
- Digital signatures  
- AEAD modes (e.g., AES-GCM)  

---

## 10. Cryptographic Strength Factors

Security depends on:
- Algorithm strength  
- Key length  
- Mode of operation  
- Key management  
- Random number generation  
- Implementation quality  

Most cryptographic failures result from:
- Weak keys  
- Poor randomness  
- Key reuse  
- Deprecated algorithms  
- Bad implementations  

Not because AES itself is broken.

---

## 11. Real-World Weaknesses

Common security issues:
- DES still enabled  
- 3DES still allowed  
- TLS 1.0/1.1 enabled  
- ECB mode used  
- Weak RSA key sizes (< 2048 bits)  
- Nonce reuse in AES-GCM  
- Reused IVs in CBC  

Attackers look for:
- Downgrade attacks  
- Weak cipher suites  
- Misconfigured certificates  

---

## CDSA-Level Interview Questions

1. Difference between symmetric and asymmetric encryption?  
2. Why is AES preferred over DES?  
3. Why is ECB insecure?  
4. What is AEAD?  
5. Why combine asymmetric and symmetric encryption?  
6. What is the role of IV?  
7. What happens if AES-GCM nonce is reused?  
8. Why is key management more important than algorithm choice?
