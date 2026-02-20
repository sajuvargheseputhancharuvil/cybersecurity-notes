# Module 3 – INTRODUCTION TO NETWORKING  
## 3.11 MAC Addresses & ARP – Layer 2 Foundations for Security (CDSA-Focused Notes)

MAC addresses operate at Layer 2 (Data Link Layer) and are responsible for communication within the same local network.

If IP addressing is logical routing (Layer 3), MAC addressing is physical delivery (Layer 2).

---

## 1. What is a MAC Address?

A MAC (Media Access Control) address:
- 48 bits (6 bytes)  
- Written in hexadecimal  
- Assigned to network interfaces (NICs)  
- Used for local delivery of frames  

Example formats:

DE:AD:BE:EF:13:37
DE-AD-BE-EF-13-37
DEAD.BEEF.1337

Binary example:

11011110 10101101 10111110 11101111 00010011 00110111

---

## 2. Standards Using MAC Addresses

MAC addressing applies to multiple technologies:
- Ethernet (IEEE 802.3)  
- Wi-Fi (IEEE 802.11)  
- Bluetooth (IEEE 802.15)  

Each network interface has its own MAC address.

**Important:**  
MAC addresses are burned in by manufacturers but can be spoofed in software.

---

## 3. MAC Address Structure

A MAC address has two parts:

**OUI (First 3 Bytes)**  
- Assigned by IEEE  
- Identifies manufacturer  

Example: DE:AD:BE

**NIC Portion (Last 3 Bytes)**  
- Unique per device  
- Assigned by manufacturer  

---

## 4. MAC & Packet Delivery

When a device sends traffic:
- If destination is in the same subnet → send directly to target MAC.  
- If destination is in another subnet → send to router’s MAC (default gateway).  

IP packets are wrapped inside Ethernet frames.

Each frame contains:
- Source MAC  
- Destination MAC  
- Payload (IP packet)  

---

## 5. Special MAC Address Types

### Unicast
- Last bit of first octet = 0  
- Sent to one specific host  

Example: DE:AD:BE:EF:13:37

### Multicast
- Last bit of first octet = 1  
- Delivered to multiple subscribed devices  

Common prefix: 01:00:5E

Used in:
- Streaming  
- Routing protocols  
- Group communication  

### Broadcast

FF:FF:FF:FF:FF:FF

Sent to:
- All devices in subnet  

Used by:
- ARP  
- DHCP  

---

## 6. Globally vs Locally Administered MAC

The second least significant bit in the first octet determines the type:

| Bit | Meaning                     |
|-----|-----------------------------|
| 0   | Globally assigned (IEEE OUI) |
| 1   | Locally administered        |

Locally administered MACs are commonly used in:
- Virtual machines  
- MAC spoofing  
- Testing environments  

---

## 7. MAC Address Attack Vectors

MAC addresses are not security mechanisms. They are easily spoofed.

### 7.1 MAC Spoofing
Attacker changes MAC to:
- Bypass MAC filtering  
- Impersonate legitimate devices  
- Evade detection  

### 7.2 MAC Flooding
Attacker floods a switch with fake MAC addresses.

Result:
- Switch MAC table fills up  
- Switch falls back to hub-like behavior  
- Traffic is broadcast to all ports  
- Enables packet sniffing  

### 7.3 MAC Filtering Bypass
MAC-based access control can be bypassed by spoofing allowed MAC addresses.

---

## 8. Address Resolution Protocol (ARP)

ARP maps: IP Address → MAC Address

ARP operates only inside the local network.

### ARP Request (Broadcast)

Example: Who has 10.129.12.101? Tell 10.129.12.100

Broadcast to: FF:FF:FF:FF:FF:FF

### ARP Reply (Unicast)

Example: 10.129.12.101 is at AA:AA:AA:AA:AA:AA

Sent directly to the requester.

---

## 9. Why ARP Exists

IP operates at Layer 3.  
Ethernet operates at Layer 2.  

ARP bridges the gap between:

Layer 3 (IP) → Layer 2 (MAC)

Without ARP, devices would not know which MAC address to use for packet delivery.

---

## 10. ARP Spoofing (Critical Security Concept)

ARP spoofing (ARP poisoning) occurs when an attacker sends fake ARP replies.

Goal:
- Associate attacker’s MAC with:
  - The gateway IP, or  
  - Another host’s IP  

Result:
Victim sends traffic to attacker instead of the real destination.

Example:
Attacker claims:

Gateway IP is at CC:CC:CC:CC:CC:CC

Victim updates ARP cache and routes traffic via attacker.

### What This Enables
- Man-in-the-Middle (MITM)  
- Credential theft  
- Session hijacking  
- Traffic manipulation  
- DNS spoofing  
- SSL stripping  

---

## 11. Detection Indicators

In packet captures:
- Multiple ARP replies for the same IP  
- Gratuitous ARP storms  
- MAC address change for gateway  
- Duplicate IP-MAC mappings  

Common attacker tools:
- Ettercap  
- Cain & Abel  
- arpspoof  

---

## 12. Defense Against ARP Attacks

- Static ARP entries (critical systems)  
- Dynamic ARP Inspection (DAI)  
- VLAN segmentation  
- IDS/IPS monitoring  
- Switch port security  
- Use encrypted protocols (TLS/IPsec)  

Even if MITM occurs, encryption limits impact.

---

## 13. CDSA Interview Questions

1. What is the size of a MAC address?  
2. What is an OUI?  
3. What is ARP?  
4. Difference between ARP request and reply?  
5. What is ARP spoofing?  
6. How do you detect ARP poisoning?  
7. What happens during MAC flooding?
