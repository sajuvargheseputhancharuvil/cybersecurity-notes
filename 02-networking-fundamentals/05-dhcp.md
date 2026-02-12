# Dynamic Host Configuration Protocol (DHCP)

DHCP is one of the most important foundational services in any IP network.

Without DHCP:
- Devices would require manual IP configuration  
- IP conflicts would be common  
- Network management would not scale  

**Defensive perspective:**  
If DHCP fails or is abused, large portions of the network are impacted.

---

## What is DHCP?

DHCP (Dynamic Host Configuration Protocol) automatically assigns:

- IP address  
- Subnet mask  
- Default gateway  
- DNS server  

to devices when they join a network.  
It removes the need for manual IP configuration.

---

## Why DHCP is Important

- Prevents duplicate IP addresses  
- Reduces administrative overhead  
- Automatically reuses unused IPs  
- Enables plug-and-play networking  

In enterprise environments, DHCP is mission-critical.

---

## DHCP Roles

| Role          | Description                                      |
|---------------|--------------------------------------------------|
| DHCP Server   | Assigns IP addresses and configuration           |
| DHCP Client   | Requests network configuration                  |

The DHCP server maintains:
- A pool of available IP addresses  
- Configuration parameters  
- Lease durations  

In small networks, the router often acts as the DHCP server.

---

## How DHCP Works – The DORA Process

The DHCP allocation process is known as **DORA**:

**Discover → Offer → Request → Acknowledge**

---

### Step-by-Step

**1. Discover (Broadcast)**  
- Client has no IP  
- Broadcasts: *“Is there a DHCP server available?”*

**2. Offer**  
- Server proposes:
  - IP address  
  - Lease time  
  - Network configuration  

**3. Request**  
- Client accepts the offered IP  
- Prevents multiple DHCP servers from assigning conflicting IPs  

**4. Acknowledge (ACK)**  
- Server confirms assignment  
- Lease becomes active  
- Client is now operational on the network  

**Traffic pattern (typical):**
- Discover → Broadcast  
- Offer → Broadcast  
- Request → Broadcast  
- ACK → Unicast  

---

## DHCP Lease Concept

IP addresses are temporary and assigned with a lease time.

**Example:**
- Lease duration: 24 hours  
- Client renews before expiration  

### Lease Renewal

- Client requests renewal  
- Server acknowledges → lease extended  
- If renewal fails → IP returns to the pool  

---

## Practical Example

A laptop connects to the office network:

1. Client broadcasts Discover  
2. Server offers `192.168.1.10`  
3. Client requests `192.168.1.10`  
4. Server acknowledges  

The device now:
- Has an IP  
- Can access internal resources  
- Can reach the internet  

---

## Security Implications of DHCP (CDSA-Critical)

DHCP is often overlooked but frequently abused.

### Common DHCP Attacks

**Rogue DHCP Server**
- Attacker deploys fake DHCP server  
- Assigns malicious gateway or DNS  
- Enables man-in-the-middle attacks  

**DHCP Starvation**
- Floods DHCP server with fake MAC requests  
- Exhausts IP pool  
- Legitimate clients cannot obtain IPs  

**DHCP Spoofing**
- Attacker responds faster than legitimate DHCP server  
- Clients accept malicious network configuration  

---

### Defensive Controls

- DHCP Snooping (managed switches)  
- Port security  
- Network segmentation  
- DHCP log monitoring  

> **CDSA interview note:**  
> DHCP snooping builds trusted IP-to-MAC bindings and blocks unauthorized DHCP responses.

---

## Protocol & Layer Mapping

- OSI Layer: Application  
- Transport: UDP  
- Server Port: **67**  
- Client Port: **68**  

DHCP relies on broadcast because clients do not yet have an IP address.

---

## Troubleshooting Perspective

If a device shows:
- “Limited connectivity”  
- IP address in the range `169.254.x.x`

This indicates:
- DHCP failure  
- APIPA (Automatic Private IP Addressing) fallback  

---

## Key Takeaways (CDSA)

- DHCP automates IP allocation  
- DORA = Discover, Offer, Request, Acknowledge  
- IP leases are temporary  
- Uses UDP ports 67/68  
- Rogue DHCP is a real-world threat  
- DHCP logs are valuable in investigations  

---

## Interview-Ready Questions

Be ready to answer:

1. What is DHCP and why is it used?  
2. Explain the DORA process  
3. What happens when DHCP fails?  
4. What is a DHCP lease?  
5. What is DHCP starvation?  
6. How does DHCP snooping protect a network?
