Networks can be categorized based on:
- Geographic scope  
- Technology used  
- Access method  
- Purpose  

In practice, you’ll mostly hear **WAN, LAN, WLAN, and VPN**.  
The other classifications (GAN, MAN, WPAN, etc.) are more academic but still useful to understand conceptually.

---

## 1. Common Terminology (What You’ll Actually Hear in Practice)

| Network Type | Meaning (Practical View) |
|-------------|---------------------------|
| WAN | The Internet or large interconnected networks |
| LAN | Internal network (home/office) |
| WLAN | LAN over Wi-Fi |
| VPN | Virtual connection into another network |

---

## 2. WAN (Wide Area Network)

In most real-world usage:

> **WAN = The Internet**

But technically:
- A WAN is multiple LANs connected together  
- Not limited to the public Internet  

Large enterprises may operate:
- Internal WAN  
- Intranet  
- Air-gapped WAN  

### Identifying a WAN

Typical characteristics:
- Uses WAN routing protocols (e.g., BGP)  
- Public (non-RFC1918) IP addressing  
- Interconnects multiple networks geographically  

**Private IP ranges (RFC 1918):**
- `10.0.0.0/8`  
- `172.16.0.0/12`  
- `192.168.0.0/16`  

If traffic leaves these ranges and routes externally → likely WAN.

### Security Relevance

WAN exposure introduces:
- Public attack surface  
- DDoS risks  
- Routing attacks  
- BGP hijacking risks  

**WAN = High exposure boundary.**

---

## 3. LAN / WLAN

**LAN (Local Area Network):**
- Internal network  
- Private IP addressing (RFC 1918)  
- Limited geographic range  

**WLAN:**
- Same as LAN  
- Uses wireless transmission (Wi-Fi)  

There is no structural difference between LAN and WLAN except:

> WLAN introduces wireless security risks.

### LAN Characteristics
- Private addressing  
- Controlled environment  
- Easier segmentation  
- Typically high-speed  

In rare cases (colleges, hotels):
- Public IPs may be assigned internally.

### Security Relevance

**LAN:**
- Lateral movement risk  
- ARP spoofing  
- Broadcast attacks  

**WLAN:**
- Rogue access points  
- Deauthentication attacks  
- Weak encryption issues  

---

## 4. VPN (Virtual Private Network)

Goal of all VPN types:

> Make a device or network appear as if it is locally connected somewhere else.

### 1. Site-to-Site VPN
- Network device ↔ Network device  
- Router/Firewall ↔ Router/Firewall  
- Entire subnets connected  

Used for:
- Connecting branch offices  
- Linking corporate locations  

Effect:
- Remote site behaves as local network  

### 2. Remote Access VPN
- Individual user connects to network  
- Creates virtual interface (TUN/TAP)  

Example:
- OpenVPN creates a virtual adapter  

Important concept:
- Routing table changes after connection  

#### Split Tunnel vs Full Tunnel

**Split Tunnel:**
- Only specific subnets routed via VPN  
- Internet traffic goes directly to ISP  

**Full Tunnel:**
- All traffic routed through VPN  
- Company can monitor internet usage  

**Security Considerations**

Split tunnel risks:
- Malware traffic bypasses corporate monitoring  

Full tunnel:
- Better monitoring  
- Higher bandwidth consumption  

### 3. SSL VPN
- Browser-based VPN  
- Often streams:
  - Applications  
  - Remote desktops  

Common in:
- Enterprise remote work  
- Browser-based lab environments  

---

## 5. Book Terms (Less Common in Practice)

These terms are mostly used academically.

### GAN (Global Area Network)
- Worldwide network  
- Internet is a GAN  
- Large international enterprise networks  

Uses:
- Fiber infrastructure  
- Subsea cables  
- Satellite links  

**GAN = WAN at global scale.**

### MAN (Metropolitan Area Network)
- Connects multiple LANs within a city/region  
- Uses high-speed fiber links  
- Often built by telecom providers  

Example:
- Company branches in same city connected via leased lines  

### PAN (Personal Area Network)
- Very short range  
- Cable-based device connections  

Example:
- Laptop connected to phone via USB  

### WPAN (Wireless Personal Area Network)
- Bluetooth-based networks  
- Very short range (few meters)  

Examples:
- Bluetooth headphones  
- Smart home devices  

Common IoT protocols:
- ZigBee  
- Z-Wave  
- Insteon  

---

## 6. Practical Comparison Summary

| Type | Scope | Example |
|------|-------|---------|
| LAN | Local building | Office network |
| WLAN | Local wireless | Home Wi-Fi |
| WAN | Large-scale | Internet |
| VPN | Logical overlay | Remote worker access |
| MAN | City-wide | Branch interconnect |
| GAN | Global | Internet |
| WPAN | Personal short-range | Bluetooth |

---

## 7. Defensive Analyst Perspective (CDSA Focus)

Understanding network types helps identify:
- Trust boundaries  
- Exposure levels  
- Routing complexity  
- Attack surface size  

Examples:
- LAN compromise → internal pivoting  
- WAN exposure → perimeter defense required  
- VPN misuse → lateral movement risk  
- WPAN → IoT monitoring challenges  

---

## 8. Interview Questions to Prepare

1. Difference between LAN and WAN?  
2. What is a split tunnel VPN?  
3. What is RFC 1918?  
4. Difference between Site-to-Site and Remote Access VPN?  
5. What risks does WLAN introduce?  
6. What is MAN vs WAN?  
