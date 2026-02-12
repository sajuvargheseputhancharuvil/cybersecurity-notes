# Network Address Translation (NAT)

NAT is one of the most important mechanisms keeping the modern IPv4 internet functioning.

Without NAT:
- Public IPv4 addresses would have been exhausted much earlier  
- Home and enterprise networks would require public IPs for every device  

**Defensive perspective:**  
NAT hides internal network structure and provides a basic boundary control (obscurity, not security).

---

## Why NAT Exists – The IPv4 Problem

IPv4 provides ~4.3 billion addresses.

Due to:
- Massive internet growth  
- Mobile device explosion  
- IoT expansion  

IPv4 address space became insufficient.

NAT was introduced as a practical workaround to:
- Allow many private devices to share one public IP  

---

## Public vs Private IP Addresses

### Public IP Address
- Globally unique  
- Assigned by ISP  
- Routable on the internet  
- Reachable from anywhere (unless firewalled)  

Examples:
- `8.8.8.8` (public DNS)  
- Public web servers  

### Private IP Address (RFC 1918)

Used only inside local networks.  
Not routable on the internet.

| Range                    | Typical Use        |
|--------------------------|--------------------|
| 10.0.0.0 – 10.255.255.255 | Large networks     |
| 172.16.0.0 – 172.31.255.255 | Medium networks |
| 192.168.0.0 – 192.168.255.255 | Home / small office |

Private addresses:
- Can be reused across different networks  
- Must be translated before internet access  

---

## What is NAT?

Network Address Translation (NAT) is performed by a router or firewall to:

- Modify IP addresses in packet headers  
- Translate private IP → public IP  
- Maintain a translation table  

NAT typically occurs at the network edge.

---

## How NAT Works (Step-by-Step Example)

**Network Example**

| Device             | IP Address        |
|--------------------|-------------------|
| Laptop             | 192.168.1.10      |
| Smartphone         | 192.168.1.11      |
| Router (LAN)       | 192.168.1.1       |
| Router (WAN/Public)| 203.0.113.50      |

### Outbound Traffic Flow

1. Laptop sends packet  
   - Source IP: `192.168.1.10`  
   - Destination IP: Public web server  

2. Router performs NAT  
   - Replaces source IP with `203.0.113.50`  
   - Assigns a temporary source port  

3. Packet traverses the internet  

4. Web server replies to  
   - `203.0.113.50`  

5. Router checks NAT table  
   - Maps public port → internal device  
   - Rewrites destination IP to `192.168.1.10`  
   - Forwards packet internally  

NAT modifies packet headers while preserving session mapping.

---

## NAT Table (Critical Concept)

Routers maintain mappings such as:

| Public IP:Port       | Private IP:Port      |
|---------------------|----------------------|
| 203.0.113.50:4444   | 192.168.1.10:5555    |

This allows:
- Multiple internal devices  
- Single public IP  
- Simultaneous connections  

This behavior is called **PAT (Port Address Translation)**.

---

## Types of NAT

### Static NAT
- One-to-one mapping  
- Permanent private → public IP mapping  

Used for:
- Exposing internal servers  

Example:  
`192.168.1.100 → 203.0.113.60`

---

### Dynamic NAT
- Uses pool of public IPs  
- Temporary one-to-one mapping  
- Less common in home networks  

---

### Port Address Translation (PAT) – Most Common
Also known as **NAT Overload**

- Many private IPs  
- One public IP  
- Differentiated by port numbers  

Used in:
- Home routers  
- Small office networks  

---

## Security Implications of NAT (CDSA-Critical)

### Benefits
- Conserves IPv4 addresses  
- Hides internal IP scheme  
- Blocks unsolicited inbound connections by default  

> NAT provides **obscurity**, not true security.

---

### Trade-Offs
- Breaks end-to-end connectivity  
- Complicates VoIP and P2P applications  
- Requires port forwarding for inbound services  
- Makes troubleshooting more complex  

---

### Common Security Considerations

**Port Forwarding Risks**
- Exposing ports like:
  - 22 (SSH)  
  - 3389 (RDP)  
- Directly exposes internal hosts  

**NAT Traversal Abuse**
- UPnP misconfigurations  
- STUN/TURN in VoIP contexts  

**Logging Challenges**
- External logs show only public IP  
- NAT logs required for attribution  
- Complicates forensics and incident response  

---

## NAT in Layer Context

NAT operates primarily at:

- Layer 3 (IP modification)  
- Layer 4 (Port modification in PAT)  

It modifies:
- Source IP  
- Source port  
- Sometimes destination values (for inbound rules)

---

## Key Takeaways (CDSA)

- NAT allows many devices to share one public IP  
- Private IPs are not internet-routable  
- PAT is the most common NAT implementation  
- NAT maintains a translation table  
- Port forwarding exposes internal systems  
- NAT complicates forensic attribution  

---

## Interview-Ready Questions

Be prepared to answer:

1. Why is NAT needed?  
2. Difference between Static NAT and PAT?  
3. What is RFC 1918?  
4. Does NAT provide security?  
5. What problems can NAT cause?  
6. How does NAT affect forensic investigation?
