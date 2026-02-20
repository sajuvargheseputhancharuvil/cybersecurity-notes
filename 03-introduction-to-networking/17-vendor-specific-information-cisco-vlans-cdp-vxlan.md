# Module 3 – INTRODUCTION TO NETWORKING  
## 3.17 Vendor-Specific Information (Cisco IOS, VLANs, CDP, VXLAN – CDSA-Focused Notes)

This section moves from theory to real enterprise implementations.

For CDSA and real-world defensive roles, you must understand:
- How Cisco devices operate  
- How VLANs are implemented  
- How tagging works (802.1Q)  
- How VLAN attacks happen  
- How CDP and STP appear in traffic  

---

## 1. Cisco IOS – What It Is & Why It Matters

Cisco IOS is the operating system used on:
- Cisco routers  
- Cisco switches  
- Some firewalls  

It provides:
- Routing (OSPF, BGP)  
- Switching (VLANs, STP)  
- ACLs  
- QoS  
- IPv6  
- VRF  
- VPLS  

### Management Methods
- CLI (most common)  
- GUI  
- Telnet (insecure)  
- SSH (secure)  

Typical remote access banner:

User Access Verification
Password:

If you see that during enumeration → likely Cisco IOS.

---

## 2. Cisco Password Types (Security-Relevant)

| Type            | Purpose           | Security Level              |
|-----------------|-------------------|-----------------------------|
| User            | Basic login       | Weak                        |
| Enable password | Privileged mode   | Weak (plaintext / Type 7)   |
| Enable secret   | Privileged mode   | Encrypted (stronger)        |
| Secret          | Secures services  | Encrypted                   |

Important:  
`enable secret` is more secure than `enable password`.

Misconfigured Cisco passwords are common pentest findings.

---

## 3. VLANs – Logical Network Segmentation

VLAN = Virtual LAN

They:
- Create logical broadcast domains  
- Segment networks without physical separation  
- Reduce broadcast traffic  
- Improve security  

Each VLAN:
- Has its own subnet  
- Is its own broadcast domain  

Example segmentation:

| Department | VLAN | Subnet            |
|-----------|------|-------------------|
| Servers   | 10   | 192.168.1.0/24    |
| Finance   | 30   | 192.168.3.0/24    |
| HR        | 40   | 192.168.4.0/24    |

---

## 4. VLAN Ranges (Cisco)

- 1–4094 usable  
- VLAN 1 = default (should not be altered)  
- 1002–1005 reserved  
- 0 & 4095 reserved  

Normal-range VLANs (2–1001) stored in `vlan.dat`.

---

## 5. VLAN Membership Types

### Static VLAN (More Secure)
- Admin assigns port manually  
- Port permanently tied to VLAN  
- Recommended approach  

### Dynamic VLAN (Riskier)
- VLAN assigned based on MAC  
- Uses VMPS  
- Vulnerable to MAC spoofing  

Attackers can:
- Spoof MAC  
- Join restricted VLAN  

Static VLANs are safer.

---

## 6. Access vs Trunk Ports

### Access Port
- Carries one VLAN  
- Used for endpoints  
- Untagged traffic  

### Trunk Port
- Carries multiple VLANs  
- Used between switches  
- Tagged traffic (802.1Q)  

Trunks are common attack targets.

---

## 7. VLAN Tagging – 802.1Q

Standard Ethernet frames do not include VLAN info.

802.1Q inserts a VLAN tag.

### 802.1Q Header Fields
- TPID = 0x8100  
- PCP (priority)  
- DEI  
- VID (VLAN ID – 12 bits)  

12-bit VID → 4094 VLANs possible.

Wireshark filter:

vlan
vlan.id == 10

tshark enumeration:

tshark -r file.pcap -T fields -e vlan.id

---

## 8. VLAN Attacks

### VLAN Hopping (DTP Abuse)

Attack uses:
- Dynamic Trunking Protocol (DTP)  
- Switch auto-negotiation  

Attacker:
1. Spoofs switch  
2. Forces trunk negotiation  
3. Gains access to multiple VLANs  

Requires:
- DTP enabled  
- Physical port access  

Tool example:  
Yersinia  

Mitigation:
- Disable DTP  
- Force access mode  
- Disable unused ports  

---

### Double Tagging Attack

Steps:
1. Attacker sends frame with two VLAN tags  
2. First switch strips outer tag  
3. Inner tag remains  
4. Packet reaches unintended VLAN  

Condition:  
Attacker must be in native VLAN of trunk.

Mitigation:
- Avoid using VLAN 1  
- Change native VLAN  
- Disable native VLAN on trunks  

---

## 9. VXLAN – Data Center Scaling

Problem:  
802.1Q supports only 4094 VLANs.

VXLAN = Layer 2 over Layer 3 overlay

Uses:
- 24-bit VNI (VXLAN Network Identifier)  
- ~16 million segments  

Designed for:
- Large-scale virtualization  
- Multi-data center connectivity  
- Cloud environments  

---

## 10. VLAN-Capable NICs

Some NICs can tag traffic directly.

### Linux VLAN Creation

sudo modprobe 8021q
sudo ip link add link eth0 name eth0.20 type vlan id 20
sudo ip addr add 192.168.1.1/24 dev eth0.20
sudo ip link set up eth0.20

### Windows VLAN (PowerShell)

Set-NetAdapter -Name “Ethernet 2” -VlanID 10

Requires VLAN-capable adapter.

---

## 11. CDP – Cisco Discovery Protocol

Layer 2 Cisco proprietary protocol.

Used for:
- Device discovery  
- Topology mapping  

CDP reveals:
- Device name  
- IP address  
- IOS version  
- Platform  
- Port ID  
- Capabilities  

Security issue:  
Information disclosure.

Recommendation:  
Disable CDP on untrusted interfaces.

---

## 12. STP – Spanning Tree Protocol

Purpose:
Prevent Layer 2 loops.

Prevents:
- Broadcast storms  
- MAC table instability  
- Network meltdown  

Rapid STP = 802.1w.

---

## CDSA-Level Takeaways

You must understand:
- VLAN tagging (802.1Q)  
- Access vs trunk ports  
- DTP risks  
- Double tagging attacks  
- CDP information leakage  
- STP loop prevention  

Common misconfigurations:
- Native VLAN = 1  
- DTP enabled  
- Trunk allowed on user ports  
- CDP enabled externally  
- No ACL between VLANs  

---

## Interview Questions

1. What is VLAN hopping?  
2. What is the difference between access and trunk port?  
3. How many VLANs does 802.1Q support?  
4. What is the native VLAN?  
5. Why disable DTP?  
6. What does CDP expose?  
7. Why is VLAN 1 risky?  
8. Difference between VLAN and VXLAN?
