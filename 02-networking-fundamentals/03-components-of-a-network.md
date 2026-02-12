# Components of a Network

This section explains what physically and logically builds a network.

**Why this matters for defenders:**
- Each component is a potential attack vector  
- Misconfiguration at any level can lead to compromise  
- Incident investigation often begins by identifying which component failed  

---

## Core Network Components (High-Level View)

A functioning network typically includes:

1. End Devices (Hosts)  
2. Intermediary Devices  
3. Network Media & Software Components  
4. Servers  

**Traffic flow model:**

End devices generate traffic → Intermediary devices move traffic → Media carries traffic → Servers provide services

---

## End Devices (Hosts)

**Definition:**  
Any device that sends or receives data on a network.

**Examples:**  
- Laptops  
- Smartphones  
- Tablets  
- IoT devices  
- Smart TVs  

**Role:**  
- Generate data (browsing, email, uploads)  
- Consume data (streaming, downloads)  
- Act as the user interface to the network  

**Security perspective:**  
End devices are:
- Most frequently compromised  
- Primary entry points for malware  
- Targets of phishing  
- Sources of lateral movement  

**Common risks:**  
- Weak endpoint security  
- Unpatched OS/software  
- Rogue IoT devices  

> **CDSA insight:** Many breaches start at the endpoint, not the server.

---

## Network Interface Card (NIC)

**What is a NIC?**  
A hardware component that allows a device to connect to a network.

**Key points:**  
- Physical interface to the network  
- Unique MAC address  
- Wired (Ethernet) or wireless (Wi-Fi)  

**Security relevance:**  
- MAC spoofing  
- Device tracking using MAC addresses  
- NIC misconfiguration exposing services  

---

## Intermediary Devices

Devices that move traffic between end devices or networks.  
They operate at different OSI layers.

---

### Router (Layer 3 – Network Layer)

**Function:**  
- Forwards packets between networks  
- Uses IP addresses  
- Maintains routing tables  

**Routing protocols (interview-relevant):**  
- OSPF  
- BGP  

**Security functions:**  
- ACLs  
- Basic firewall capabilities  
- Traffic management  

**Security importance:**  
- Misconfigured routers expose internal networks  
- Targets for DDoS  
- Routing manipulation attacks  

---

### Switch (Layer 2 – Data Link Layer)

**Function:**  
- Connects devices within a LAN  
- Uses MAC addresses  
- Forwards frames to intended recipients  

**Why better than hubs:**  
- Reduced collisions  
- Improved efficiency  
- Intelligent forwarding  

**Security risks:**  
- ARP spoofing  
- MAC flooding  
- VLAN hopping  

> Switch-level attacks are common during internal compromise.

---

### Hub (Layer 1 – Physical Layer)

**Function:**  
- Broadcasts traffic to all ports  
- No intelligence or filtering  

**Why rarely used today:**  
- Causes collisions  
- Inefficient  
- No traffic control  

**Security impact:**  
- Easy packet sniffing  
- No isolation between devices  

---

### Wireless Access Points

**Role:**  
- Provide Wi-Fi connectivity  
- Bridge wireless clients to wired networks  

**Security risks:**  
- Evil twin attacks  
- Rogue access points  
- Weak encryption (WEP/WPA misconfiguration)  

---

## Network Media & Transmission

### Network Media

**Wired:**  
- Twisted pair (Ethernet)  
- Coaxial  
- Fiber optic (high-speed backbone)  

**Wireless:**  
- Wi-Fi (radio)  
- Bluetooth  
- Microwave / satellite  

**Security considerations:**  
- Wired networks can be physically tapped  
- Wireless traffic can be intercepted remotely  
- Fiber is harder (but not impossible) to tap  

---

### Cabling & Connectors

- RJ-45 connectors for Ethernet  
- Cable quality impacts speed and reliability  

**Poor cabling leads to:**  
- Packet loss  
- Performance bottlenecks  
- Troubleshooting complexity  

---

## Network Protocols (Operational Rules)

Protocols define how devices communicate:

- Segmentation  
- Addressing  
- Routing  
- Error detection  
- Synchronization  

**Key protocols:**  
- TCP/IP – foundation of the internet  
- HTTP/HTTPS – web communication  
- FTP – file transfer  
- SMTP – email  

> **Security note:** Unencrypted protocols expose data in transit.

---

## Network Management Software

Used to:
- Monitor performance  
- Detect faults  
- Configure devices  
- Enforce security policies  

**Defensive importance:**  
- Traffic monitoring  
- Anomaly detection  
- Log analysis  
- Configuration auditing  

Often integrated with:
- SIEM  
- IDS/IPS  
- Monitoring dashboards  

---

## Software Firewalls (Host-Based Firewalls)

Firewalls running on individual devices.

**Functions:**  
- Monitor inbound and outbound traffic  
- Block suspicious connections  
- Enforce application-level rules  

**Security significance:**  
- Protects even if perimeter controls fail  
- Limits lateral movement  
- Reduces exposed services  

> **CDSA concept:** Defense-in-depth requires host-level and network-level controls.

---

## Servers

**Definition:**  
Systems that provide services to clients.

**Types:**  
- Web servers  
- File servers  
- Mail servers  
- Database servers  

**Core functions:**  
- Host applications  
- Centralized storage  
- Authentication services  
- Resource sharing  

**Client–Server Model:**  
Client sends request → Server processes → Server responds  

**Security perspective:**  
Servers are:
- High-value targets  
- Data concentration points  
- Authentication control planes  

**Common risks:**  
- Misconfigured services  
- Weak authentication  
- Open ports  
- Unpatched vulnerabilities  

> Compromised servers lead to high-impact incidents.

---

## Big Picture Summary

| Component        | Role                    | Security Focus            |
|------------------|--------------------------|----------------------------|
| End Devices      | Generate/consume data    | Endpoint protection        |
| NIC              | Network interface        | MAC spoofing               |
| Switch           | Internal LAN traffic     | ARP/VLAN attacks           |
| Router           | Connects networks        | ACLs, exposure control     |
| Media            | Data transmission        | Physical/wireless tapping  |
| Software Firewall| Host-level protection    | Traffic filtering          |
| Server           | Service provider         | Hardening and patching     |

---

## Defensive Analyst Takeaways (CDSA)

- Most attacks begin at end devices  
- Intermediary devices are choke points for visibility  
- Routers and switches must be securely configured  
- Host firewalls provide critical second-layer defense  
- Servers are high-value assets requiring strict hardening  
- Network visibility depends on understanding each component  

---

## Interview-Ready Questions

Be ready to answer:

1. What is the difference between a router and a switch?  
2. What OSI layer does a switch operate at?  
3. What is a NIC and why is a MAC address important?  
4. What is the client–server model?  
5. Why are software firewalls important even with perimeter firewalls?  
6. Why are hubs insecure compared to switches?
