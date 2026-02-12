# Network Communication

For communication to work correctly in a network, three core elements must function together:

- **MAC Address** → Identifies a device on the local network  
- **IP Address** → Identifies a device across networks  
- **Port Number** → Identifies a specific service or process  

**Analogy (for intuition):**  
- IP = Building address  
- MAC = Apartment door  
- Port = Specific person inside the apartment  

Understanding this trio is critical for:
- Packet analysis  
- Traffic monitoring  
- Incident investigation  
- Firewall rule creation  

---

## MAC Address (Layer 2 – Data Link)

### What is a MAC Address?

A MAC (Media Access Control) address is a unique hardware identifier assigned to a NIC.

- 48 bits (6 bytes)  
- Hexadecimal format (e.g., `00:1A:2B:3C:4D:5E`)  
- First 24 bits → Manufacturer (OUI)  
- Last 24 bits → Device-specific  

Operates at **OSI Layer 2**.

---

### How MAC Addresses Work (Inside a LAN)

When Device A sends data to Device B in the same LAN:

1. Device A knows the destination IP  
2. Uses **ARP** to resolve IP → MAC  
3. Sends an Ethernet frame with the destination MAC  
4. The switch forwards the frame using its MAC table  

**Local LAN communication flow:**
- ARP request → Broadcast  
- ARP reply → Unicast  
- Frame delivery → Switch forwards to correct port  

---

### Security Relevance (Layer 2)

Common attacks:
- ARP spoofing  
- MAC flooding  
- Man-in-the-middle (MITM)  

> **CDSA concept:** MAC addresses are only meaningful within the local broadcast domain.

---

## IP Address (Layer 3 – Network Layer)

### What is an IP Address?

An IP address identifies a device logically across networks.

**IPv4**
- 32-bit  
- Example: `192.168.1.1`

**IPv6**
- 128-bit  
- Example: `2001:0db8:85a3::8a2e:0370:7334`

---

### Role in Communication

Routers use IP addresses to:
- Determine routing paths  
- Forward packets between networks  
- Route traffic across the internet  

Unlike MAC addresses:
- IPs can change  
- Assigned dynamically (DHCP) or statically  

---

### Security Relevance (Layer 3)

Common threats:
- IP spoofing  
- Network scanning  
- ICMP abuse  
- Routing manipulation  

> **CDSA note:** IP logs are foundational for incident response and attribution.

---

## Ports (Layer 4 – Transport Layer)

### What is a Port?

A port identifies a specific application or service on a device.

- Range: `0–65535`  
- Allows multiple services on one IP  
- Enables simultaneous sessions  

**Example (same server IP):**
- HTTP → 80  
- HTTPS → 443  
- SSH → 22  

---

### Port Categories

**Well-Known Ports (0–1023)**  
Reserved for standard services:
- 80 → HTTP  
- 443 → HTTPS  
- 21 → FTP  
- 25 → SMTP  

**Registered Ports (1024–49151)**  
Typically assigned to vendor applications:
- 1433 → Microsoft SQL Server  

**Dynamic / Ephemeral Ports (49152–65535)**  
Used temporarily by client systems.  
After a session ends, the port closes.

---

### Viewing Active Ports

Common commands:
- `netstat`  
- `ss` (modern Linux alternative)  

Used for:
- Identifying listening services  
- Detecting suspicious connections  

---

### Security Relevance (Layer 4)

- Open ports = attack surface  
- Targets for port scanning  
- Enforced by firewall rules  

> **CDSA must-know:** An open port represents potential exposure.

---

## End-to-End Web Browsing Example

### Step 1: DNS Resolution
User enters `example.com` → DNS resolves to an IP (e.g., `93.184.216.34`)

---

### Step 2: Encapsulation
- Browser creates HTTP request  
- TCP adds source/destination ports  
- IP adds source/destination IP  
- ARP resolves next-hop MAC  
- Ethernet frame is built  

---

### Step 3: Transmission
Client → Router → ISP → Multiple routers → Server  

Each router forwards based on destination IP.

---

### Step 4: Server Processing
- Server receives packet  
- Checks destination port (80/443)  
- Web server processes request  
- Generates response  

---

### Step 5: Response
- Response sent back to client’s ephemeral port  
- Routed back across the network  
- Browser renders the webpage  

---

## Communication Mapping by Layer

| OSI Layer | Identifier     | Purpose                         |
|----------|------------------|----------------------------------|
| Layer 2  | MAC Address     | Local delivery within LAN        |
| Layer 3  | IP Address      | Cross-network routing            |
| Layer 4  | Port Number     | Application/service identification |

---

## Defensive Analyst Takeaways (CDSA)

- MAC addresses matter inside LANs  
- IP addresses matter across networks  
- Ports identify services  
- ARP links IP to MAC  
- Ephemeral ports enable temporary sessions  
- Every packet contains:
  - Source IP  
  - Destination IP  
  - Source Port  
  - Destination Port  

This is known as the **5-tuple**:
- Source IP  
- Destination IP  
- Source Port  
- Destination Port  
- Protocol  

Critical for:
- SIEM correlation  
- Firewall logs  
- IDS alerts  
- Threat hunting  

---

## Interview-Ready Questions

Be ready to explain:

1. Difference between MAC and IP addresses  
2. What ARP is and why it’s needed  
3. Why ports exist  
4. What an ephemeral port is  
5. How a browser accesses a website (end-to-end)  
6. Which OSI layer ARP operates at  
