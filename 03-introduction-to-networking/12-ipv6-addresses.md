# Module 3 – INTRODUCTION TO NETWORKING  
## 3.12 IPv6 Addresses – Structure, Types & Security Relevance (CDSA-Focused Notes)

IPv6 is the successor to IPv4 and was designed to solve IPv4 exhaustion and architectural limitations.

While IPv4 is still widely used, IPv6 adoption continues to grow. Most modern systems support **Dual Stack**, meaning IPv4 and IPv6 run simultaneously.

---

## 1. Why IPv6 Exists

IPv4 limitation: 2^32 ≈ 4.3 billion addresses

IPv6 capacity: 2^128 ≈ 340 undecillion addresses

This effectively removes global address scarcity.

---

## 2. Core Characteristics of IPv6

| Feature            | IPv4              | IPv6                    |
|--------------------|-------------------|--------------------------|
| Address Size       | 32-bit            | 128-bit                  |
| Format             | Decimal           | Hexadecimal              |
| Address Space      | ~4.3 billion      | ~340 undecillion         |
| NAT Required       | Common            | Not required             |
| Encryption         | Optional (IPsec)  | Built-in support (IPsec) |
| Auto Configuration | DHCP              | SLAAC / DHCPv6           |

---

## 3. Key Improvements Over IPv4

- Vast address space  
- No need for NAT (true end-to-end communication)  
- Multiple IPs per interface  
- SLAAC (self-configuration)  
- Simplified header structure  
- Better routing aggregation  
- Native multicast (no broadcast)  

---

## 4. IPv6 Address Structure

IPv6 characteristics:
- 128 bits (16 bytes)  
- Divided into 8 blocks  
- Each block = 16 bits (4 hex digits)  
- Blocks separated by colons (`:`)  

Example (full form):

fe80:0000:0000:0000:dd80:b1a9:6687:2d3b/64

Shortened form:

fe80::dd80:b1a9:6687:2d3b/64

---

## 5. Shortening Rules (RFC 5952)

To simplify IPv6 notation:

1. Remove leading zeros in each block  
2. Replace consecutive zero blocks with `::`  
3. `::` can appear only once  
4. Hex letters must be lowercase  

Valid: fe80::1

Invalid: FE80::0001

---

## 6. IPv6 Address Components

An IPv6 address consists of:

**Network Prefix**  
Identifies the network/subnet.

**Interface Identifier (Suffix)**  
Identifies the host/interface.

Typical default subnet size: /64

Meaning:
- First 64 bits → network  
- Last 64 bits → host  

---

## 7. Interface Identifier Creation

Originally:
- Derived from MAC address (EUI-64 format)

Modern systems:
- Use privacy extensions  
- Generate temporary random interface IDs  

**Security Note:**  
MAC-derived IPv6 addresses can reveal:
- Hardware vendor  
- Device identity  

---

## 8. IPv6 Address Types

IPv6 eliminates broadcast and uses:

| Type      | Purpose           |
|-----------|-------------------|
| Unicast   | One-to-one        |
| Anycast   | One-to-nearest    |
| Multicast | One-to-many       |

### Unicast

Assigned to a single interface: 2001:db8::1

### Anycast

Multiple devices share the same address.  
Routing delivers packets to the nearest instance.

Common use:
- CDN  
- DNS root servers  

### Multicast

Replaces broadcast in IPv6.

Example: ff02::1

All nodes on the local network.

Used for:
- Neighbor discovery  
- Router advertisements  
- SLAAC  

---

## 9. No Broadcast in IPv6

IPv4 uses broadcast:192.168.1.255

IPv6 uses multicast instead.  
This is more efficient and reduces broadcast storm risk.

---

## 10. Hexadecimal Refresher

IPv6 uses base 16:

| Decimal | Hex | Binary |
|---------|-----|--------|
| 10      | A   | 1010   |
| 11      | B   | 1011   |
| 12      | C   | 1100   |
| 13      | D   | 1101   |
| 14      | E   | 1110   |
| 15      | F   | 1111   |

Example:

IPv4: 192.168.12.160

Hex equivalent: C0.A8.0C.A0

---

## 11. Common IPv6 Prefixes

| Prefix       | Purpose                      |
|--------------|-------------------------------|
| fe80::/10    | Link-local                    |
| ::1          | Loopback                      |
| ::           | Unspecified                   |
| 2000::/3     | Global Unicast                |
| fc00::/7     | Unique Local Address (ULA)    |
| ff00::/8     | Multicast                     |

---

## 12. Dual Stack

Most modern networks run:
- IPv4  
- IPv6  

**Security Risk:**  
IPv6 may be enabled by default but not monitored.  
Attackers can abuse IPv6 to bypass IPv4-only security controls.

---

## 13. Security Implications of IPv6

### 13.1 NAT Removal

IPv6 supports end-to-end connectivity.

Risk:
- Increased exposure if firewall rules are misconfigured.

### 13.2 SLAAC Attacks

Rogue Router Advertisements can:
- Assign malicious gateways  
- Redirect traffic  
- Enable MITM attacks  

### 13.3 IPv6 Enabled by Default

Many systems enable IPv6 even when unused.

Attackers can:
- Tunnel IPv6 traffic  
- Bypass IPv4-only monitoring  

### 13.4 Neighbor Discovery (NDP) Attacks

IPv6 replaces ARP with NDP.  
Similar spoofing and poisoning attacks are possible.

---

## 14. CDSA Interview Questions

1. What is the size of an IPv6 address?  
2. Why does IPv6 not require NAT?  
3. What replaced broadcast in IPv6?  
4. What is SLAAC?  
5. What is the default IPv6 subnet size?  
6. What is a link-local address?  
7. Why can IPv6 be a monitoring blind spot?

---

## 15. CDSA Takeaway

IPv6 is not just “bigger IPv4.” It changes:
- Addressing philosophy  
- Routing design  
- Security posture  
- Network visibility  

If IPv6 is enabled but not monitored, it becomes an attacker backdoor.

Understanding IPv6 is essential for:
- Modern network defense  
- IDS/IPS configuration  
- Firewall policy validation  
- Traffic analysis  
