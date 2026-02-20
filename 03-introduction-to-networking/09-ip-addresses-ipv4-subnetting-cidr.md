# Module 3 – INTRODUCTION TO NETWORKING  
## 3.9 IP Addresses – IPv4 Structure, Subnetting & CIDR (CDSA-Focused Notes)

An IP address allows devices to communicate across networks, not just within a single LAN.

- MAC address → Works inside the same local network (Layer 2)  
- IP address (IPv4/IPv6) → Enables communication across different networks (Layer 3)  

**Analogy:**
- IP address = Postal address (city + street)  
- MAC address = Apartment number inside the building  

If two devices are on different networks, knowing only the MAC address is useless — routing requires IP addressing.

---

## 1. What an IP Address Does

An IP address ensures:
- Unique identification of devices  
- Logical grouping into networks  
- Packet delivery from source to destination  
- Routing between subnets  

**Important rule:**  
An IP address must be unique within its network.

---

## 2. IPv4 Structure

IPv4 is:
- 32-bit address  
- Divided into 4 octets (8 bits each)  
- Written in dotted-decimal format  

**Example (Binary):**

01111111.00000000.00000000.00000001

**Decimal:**

127.0.0.1

---

## 3. IPv4 Address Capacity

Total possible IPv4 addresses:

2^32 = 4,294,967,296

Due to reservations and private ranges, usable public addresses are fewer.

---

## 4. Network Part vs Host Part

An IPv4 address consists of:
- Network portion  
- Host portion  

**Who assigns them?**
- IANA allocates public IP blocks  
- ISPs allocate to customers  
- Routers/DHCP assign host addresses locally  

---

## 5. Historical Class-Based Addressing (Legacy Concept)

Before CIDR, IPv4 used fixed classes:

| Class | Default Mask     | CIDR | Usable Hosts |
|------:|------------------|------|--------------|
| A     | 255.0.0.0        | /8   | 16,777,214   |
| B     | 255.255.0.0      | /16  | 65,534       |
| C     | 255.255.255.0    | /24  | 254          |
| D     | Multicast        | N/A  | Multicast    |
| E     | Reserved         | N/A  | Reserved     |

Modern networks use CIDR instead of fixed classes.

---

## 6. Subnet Mask

A subnet mask:
- Determines which part of IP is network  
- Determines which part of IP is host  

**Example:**

IP:192.168.10.39
Subnet Mask:255.255.255.0
Binary Mask:11111111.11111111.11111111.00000000

Meaning:
- First 24 bits → Network  
- Last 8 bits → Hosts  

---

## 7. Network Address & Broadcast Address

Each subnet reserves:
- First IP → Network address  
- Last IP → Broadcast address  

**Example: 192.168.10.0/24**

| Type         | Address          |
|--------------|------------------|
| Network      | 192.168.10.0     |
| First Usable | 192.168.10.1     |
| Last Usable  | 192.168.10.254   |
| Broadcast    | 192.168.10.255   |

### Broadcast Address

Used to:
- Send message to all hosts in subnet  
- Does not expect response  

**Examples:**
- ARP  
- DHCP Discover  

**Security relevance:**
- Broadcast storms  
- Smurf attacks  

---

## 8. Default Gateway

The default gateway:
- Is the router’s IP inside the subnet  
- Connects the subnet to other networks  

Common conventions:
- First usable IP (e.g., .1)  
- Last usable IP (e.g., .254)  

Not mandatory, but standard practice.

---

## 9. Binary System & IPv4 Conversion

Each octet uses bit values:128 64 32 16 8 4 2 1

**Example:**

192 in binary: 128 + 64 = 192
Binary: 11000000

**Full example:**

IP:192.168.10.39
Binary:11000000.10101000.00001010.00100111
Binary understanding is critical for:
- Subnetting  
- CIDR calculations  
- Network design  
- Firewall rule analysis  

---

## 10. CIDR (Classless Inter-Domain Routing)

CIDR replaces fixed class-based addressing.

Instead of:255.255.255.0
We write:/24

Meaning:
- First 24 bits are network bits  

**Example:**
192.168.10.39/24

Binary mask:11111111.11111111.11111111.00000000
CIDR suffix = number of 1s in subnet mask.

---

## 11. Why CIDR Matters

CIDR enables:
- Flexible subnet sizes  
- Efficient IP allocation  
- Reduced IP waste  
- Route aggregation  

**Examples:**
- /30 → 2 usable hosts  
- /29 → 6 usable hosts  
- /28 → 14 usable hosts  

Essential for:
- Firewall ACL design  
- Routing policies  
- Network segmentation  

---

## 12. Security Perspective (CDSA Focus)

Understanding IP addressing enables:
- Identifying lateral movement  
- Detecting abnormal subnet communication  
- Proper segmentation  
- Firewall rule validation  
- Preventing misconfigured gateways  

**Common attack vectors:**

| Attack                  | IP Concept Abused           |
|-------------------------|-----------------------------|
| IP Spoofing             | Source address manipulation|
| Subnet Misconfiguration | Lateral movement           |
| Broadcast Abuse         | Amplification attacks      |
| Improper CIDR ACL       | Unauthorized access        |

---

## 13. Interview-Level Questions

1. Difference between MAC and IP address?  
2. What is the broadcast address?  
3. What is CIDR?  
4. How many hosts in /24?  
5. What is the network address?  
6. Why are there 2 unusable IPs in a subnet?  
7. Why did class-based addressing fail?
