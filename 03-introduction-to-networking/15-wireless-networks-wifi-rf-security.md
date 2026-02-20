# Module 3 – INTRODUCTION TO NETWORKING  
## 3.15 Wireless Networks (WiFi & RF Security – CDSA-Focused Notes)

Wireless networks remove the cable — but not the risks.

From a defensive perspective, wireless means:
- Shared medium  
- Broadcast communication  
- Physically exposed attack surface  

Understanding WiFi is critical because attackers don’t need physical LAN access anymore — they just need signal range.

---

## 1. How Wireless Networks Work

Wireless networks use radio frequency (RF) signals instead of cables.

**Main bands:**
- 2.4 GHz  
- 5 GHz  

Devices communicate through a Wireless Access Point (WAP).

**Basic Flow**
1. Device sends RF signal  
2. WAP receives and processes it  
3. WAP forwards traffic to wired network or internet  
4. Reverse path for responses  

WAP acts as:
- Gateway  
- Traffic controller  
- Authentication point  

---

## 2. Wireless Network Types

| Type  | Technology     | Coverage        |
|-------|----------------|-----------------|
| WLAN  | WiFi (802.11)  | Home / Office   |
| WWAN  | 3G / 4G / 5G   | City / Region   |

---

## 3. WiFi Connection Process (802.11)

To connect to WiFi, a device needs:
- SSID (network name)  
- Authentication method  
- Password / credentials  

**Association Request Includes:**
- Device MAC address  
- SSID  
- Supported data rates  
- Supported channels  
- Supported security protocols  

Even if SSID broadcasting is disabled:
- SSID still appears in authentication traffic  

Hidden SSID ≠ Security.

---

## 4. WEP Authentication (Legacy – Broken)

WEP uses a challenge-response mechanism.

**WEP Handshake Steps**
1. Client requests association  
2. WAP sends challenge  
3. Client encrypts challenge using shared key  
4. WAP verifies response  

### Why WEP Is Insecure

Problems:
- Uses RC4 cipher  
- Small 24-bit IV  
- CRC calculated on plaintext  
- Same key used for encryption & authentication  

This allows:
- Packet manipulation  
- Plaintext recovery  
- IV brute forcing  

WEP is completely broken and must never be used.

---

## 5. Wireless Encryption Comparison

| Protocol | Security Level | Status        |
|----------|----------------|---------------|
| WEP      | Weak           | Deprecated    |
| WPA      | Improved       | Legacy        |
| WPA2     | Strong         | Standard      |
| WPA3     | Strongest      | Recommended   |

**WPA Authentication Types**

**WPA-Personal**
- Uses Pre-Shared Key (PSK)  
- Common in home networks  

**WPA-Enterprise**
- Uses authentication server (RADIUS / TACACS+)  
- Per-user credentials  
- Enterprise-grade security  

---

## 6. Authentication Protocols

**LEAP**
- Uses shared key  
- Weak  
- Cisco proprietary  
- Vulnerable to dictionary attacks  

**PEAP**
- Uses TLS tunnel  
- Encrypted authentication  
- More secure than LEAP  

**EAP-TLS (Strongest Option)**
- Uses digital certificates  
- PKI-based  
- Mutual authentication  
- No shared passwords  

Best practice for enterprise environments.

---

## 7. TACACS+ in Wireless

Used for:
- Centralized authentication  
- Authorization  
- Accounting (AAA)  

Authentication requests are encrypted to protect credentials.

Common in enterprise environments.

---

## 8. Wireless Attack Vectors

Wireless networks are highly attackable because traffic is broadcast over RF.

### Disassociation Attack
Attacker sends forged disassociation frames.

Result:
- Clients disconnect  
- Forced reconnection  
- Can lead to MITM attacks  

Often a precursor to Evil Twin attacks.

### Information Disclosure
Examples:
- SIP enumeration over WiFi  
- Exposed configuration files (SEPxxxx.cnf)  
- Weak WPA passphrases  
- SSID discovery via sniffing  

### MAC Filtering Bypass
MAC filtering is weak because:
- MAC addresses can be spoofed  
- MACs are observable in wireless traffic  

---

## 9. Wireless Hardening Measures

**Disable SSID Broadcasting**
- Reduces visibility  
- Not true protection  

**Use WPA2 or WPA3**
- Minimum requirement  
- Prefer WPA3 or WPA2-Enterprise  

**Enable MAC Filtering**
- Adds friction, not real security  

**Deploy EAP-TLS**
- Strongest enterprise option  

**Enable Firewall on WAP**
- Block unnecessary inbound connections  
- Disable unused services  

---

## 10. RF Considerations

Signal strength is affected by:
- Physical obstacles  
- Transmit power  
- RF interference  
- Environmental noise  

Security implication:
- Signals extend beyond building walls  

Physical perimeter ≠ Wireless perimeter.

---

## 11. Wireless vs Wired – Security Comparison

| Factor                  | Wired | Wireless |
|-------------------------|-------|----------|
| Medium                  | Cable | RF       |
| Physical access needed  | Yes   | No       |
| Sniffing difficulty     | Higher| Easier   |
| Attack surface          | Local | Broadcast|

Wireless is inherently more exposed.

---

## 12. CDSA-Level Takeaways

Wireless networks introduce:
- Rogue AP risks  
- Deauth attacks  
- Weak encryption risks  
- Credential capture risks  
- MITM attack opportunities  

Never rely on:
- Hidden SSID  
- MAC filtering  
- Legacy encryption  

Always enforce:
- WPA3 / WPA2-Enterprise  
- Strong authentication  
- Segmentation  
- Monitoring  

---

## 13. Interview Questions You Should Handle

1. Why is WEP broken?  
2. Difference between WPA-Personal and WPA-Enterprise?  
3. What is EAP-TLS?  
4. What is a disassociation attack?  
5. Can hidden SSID protect a network?  
6. Why is MAC filtering weak?  
7. What role does TACACS+ play?  
