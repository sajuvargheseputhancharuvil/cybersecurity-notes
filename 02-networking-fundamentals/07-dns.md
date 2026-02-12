# Domain Name System (DNS)

DNS is one of the most critical services on the internet.

Without DNS:
- Users would need to remember IP addresses  
- Browsing would be impractical  
- Most online services would fail  

**Defensive perspective:**  
DNS traffic is one of the richest sources of detection data.

---

## What is DNS?

DNS (Domain Name System) translates human-readable domain names into IP addresses.

| Domain           | IP Address       |
|------------------|------------------|
| www.example.com  | 93.184.216.34    |

DNS acts as the internet’s phonebook, bridging:
- Human-friendly names  
- Machine-readable IP addresses  

---

## Domain Names vs IP Addresses

| Term        | Description                        |
|-------------|------------------------------------|
| Domain Name | Readable name (www.example.com)    |
| IP Address  | Numeric identifier (93.184.216.34) |

Humans use domain names.  
Networks use IP addresses.

---

## DNS Hierarchy (Tree Structure)

DNS is hierarchical.

| Level                  | Example                 |
|------------------------|-------------------------|
| Root (.)               | Top of hierarchy        |
| TLD                    | .com, .org, .net        |
| Second-Level Domain    | example.com             |
| Subdomain / Hostname   | www.example.com         |

Example breakdown of `www.accounts.google.com`:
- `.` (Root)  
- `.com` (TLD)  
- `google` (Second-level domain)  
- `accounts` (Subdomain)  

---

## DNS Resolution Process (Step-by-Step)

When a user enters `www.example.com`, the system resolves the domain to an IP address.

1. **User enters URL**  
   Browser requests IP for `www.example.com`.

2. **Local cache check**  
   System checks browser and OS DNS cache.

3. **Query recursive DNS server**  
   Usually ISP resolver or public DNS (e.g., 8.8.8.8).

4. **Root server referral**  
   Root server points to `.com` TLD servers.

5. **TLD server referral**  
   TLD server points to authoritative server for `example.com`.

6. **Authoritative server response**  
   Returns final IP address.

7. **Response returned to client**  
   Client connects to `93.184.216.34`.

This entire process typically completes in milliseconds.

---

## Important DNS Concepts (CDSA)

### Recursive DNS Server
- Handles client queries  
- Performs full resolution  
- Returns final IP to client  

### Authoritative DNS Server
- Holds official DNS records  
- Source of truth for a domain  

### DNS Cache
- Improves performance  
- Reduces repeated queries  
- TTL (Time To Live) controls cache duration  

---

## DNS in Network Layers

DNS operates at:
- Application Layer  
- UDP port 53 (most queries)  
- TCP port 53 (zone transfers, large responses)  

---

## Security Implications of DNS

DNS is frequently abused in attacks.

### Common DNS Attacks

**DNS Spoofing / Poisoning**
- Attacker injects false IP addresses  
- Redirects users to malicious destinations  

**DNS Cache Poisoning**
- Corrupts recursive resolver cache  
- Impacts many users at once  

**DNS Tunneling**
- Encodes data inside DNS queries  
- Used for command-and-control and data exfiltration  

**DNS Amplification (DDoS)**
- Abuses open resolvers  
- Generates large reflection traffic  

---

## Defensive Controls

- DNS logging and monitoring  
- DNSSEC for record authentication  
- Restrict access to recursive resolvers  
- Detect suspicious domain patterns  
- Monitor high-entropy domains  

> **CDSA insight:** DNS logs are extremely valuable for threat hunting.

---

## Investigation Insight

Suspicious domains such as:

- randomstring-xy12z-commandcontrol.com

DNS telemetry may reveal:
- Newly registered domains  
- Rare TLD usage  
- High query volume  
- Beaconing patterns  

DNS often surfaces infections earlier than endpoint logs.

---

## DNS vs DHCP vs NAT

| Protocol | Purpose                          |
|----------|----------------------------------|
| DHCP     | Assigns IP addresses             |
| DNS      | Resolves names to IPs            |
| NAT      | Translates private IP to public  |

Understanding how these interact is key for troubleshooting.

---

## Key Takeaways (CDSA)

- DNS translates domain names to IP addresses  
- Operates over UDP/TCP port 53  
- Follows a hierarchical structure  
- Caching improves performance  
- Frequently abused in attacks  
- DNS logs are critical in investigations  

---

## Interview-Ready Questions

1. What is DNS?  
2. Explain the DNS resolution process.  
3. Difference between recursive and authoritative DNS servers?  
4. What is DNS cache poisoning?  
5. Why is DNS important for threat detection?  
6. Which ports does DNS use?
