# Module 3 – INTRODUCTION TO NETWORKING  
## 3.10 Subnetting – Practical Breakdown & Mental Math (CDSA-Focused Notes)

Subnetting is the process of dividing a larger IPv4 network into smaller logical networks (subnets).

A subnet:
- Shares the same network address  
- Has its own broadcast address  
- Has a defined usable host range  

**Analogy:**  
Subnetting is like dividing a large office building into departments with separate access-controlled entrances.

---

## 1. Why Subnetting Matters (Security Perspective)

Subnetting enables:
- Network segmentation  
- Reduced broadcast traffic  
- Access control enforcement  
- Attack surface reduction  
- Controlled lateral movement  

Without subnetting → flat network → easier pivoting for attackers.

---

## 2. What Subnetting Allows You to Calculate

For any subnet, you must be able to determine:
- Network address  
- Broadcast address  
- First usable host  
- Last usable host  
- Total number of hosts  

These skills are critical for:
- Firewall rule analysis  
- VPN routing troubleshooting  
- IDS traffic review  
- Lateral movement detection  

---

## 3. Example Walkthrough

**Given:**

IP Address: 192.168.12.160
Subnet Mask: 255.255.255.192
CIDR: /26

---

## 4. Step 1 – Understand the Mask

Subnet mask in binary: 11111111.11111111.11111111.11000000

CIDR: `/26`  
- First 26 bits → Network  
- Remaining 6 bits → Hosts  

---

## 5. Step 2 – Determine Total Addresses

Host bits = 6  

2^6 = 64 total addresses

Subtract:
- 1 Network address  
- 1 Broadcast address

- 62 usable hosts

---

## 6. Step 3 – Calculate Network & Broadcast

Block size formula:

256 - 192 = 64

Subnet blocks in 4th octet:

0
64
128
192

IP `192.168.12.160` falls in: 128 – 191

---

## 7. Final Answer

| Type        | Address           |
|-------------|-------------------|
| Network     | 192.168.12.128    |
| First Host  | 192.168.12.129    |
| Last Host   | 192.168.12.190    |
| Broadcast   | 192.168.12.191    |
| Total Hosts | 62                |

---

## 8. Dividing /26 into 4 Smaller Subnets

Given: 192.168.12.128/26

We want:4 subnets → 2^2 = 4

Borrow 2 bits:/26 → /28

New subnet mask:255.255.255.240

Host bits = 4  

2^4 = 16 total
14 usable per subnet

---

## 9. Resulting Subnets (/28)

Block size: 256 - 240 = 16

| Subnet | Network           | First Host | Last Host  | Broadcast         |
|--------|-------------------|------------|------------|-------------------|
| 1      | 192.168.12.128    | .129       | .142       | 192.168.12.143    |
| 2      | 192.168.12.144    | .145       | .158       | 192.168.12.159    |
| 3      | 192.168.12.160    | .161       | .174       | 192.168.12.175    |
| 4      | 192.168.12.176    | .177       | .190       | 192.168.12.191    |

---

## 10. Mental Subnetting (Fast Exam Method)

Key anchors:

/8   → 1st octet changes
/16  → 2nd octet changes
/24  → 3rd octet changes
/32  → Single host

---

## 11. Modulo Trick

CIDR remainder:

CIDR % 8 = remainder

Example: /25 → 25 % 8 = 1
Block size = 2^(8 - 1) = 128

Ranges: 

0–127
128–255

---

## 12. Block Size Quick Reference

| Remainder | Block Size |
|-----------|------------|
| 0         | 256        |
| 1         | 128        |
| 2         | 64         |
| 3         | 32         |
| 4         | 16         |
| 5         | 8          |
| 6         | 4          |
| 7         | 2          |

---

## 13. Example – /25 Quick Analysis

Given: 192.168.1.0/25

Block size: 128

Ranges:

192.168.1.0 – 127
192.168.1.128 – 255

Usable:
- Subnet 1: 1 – 126  
- Subnet 2: 129 – 254  

---

## 14. Security & CDSA Perspective

Subnetting directly impacts:
- Lateral movement difficulty  
- Broadcast domain control  
- VLAN design  
- Firewall segmentation  
- VPN route control  
- IDS monitoring scope  

**Flat networks (/24 everywhere):**
- Easy pivoting  
- Easy ARP poisoning  
- Easier credential harvesting  
- Harder traffic attribution  

**Segmented networks:**
- Force routing decisions  
- Enable ACL enforcement  
- Improve logging accuracy  
- Slow attackers down  

---

## 15. Interview-Level Questions

1. How many usable hosts in /26?  
2. What is the block size of /27?  
3. What does /25 mean?  
4. What is the broadcast of 10.0.0.64/26?  
5. Why are 2 IPs reserved?  
6. Why is subnetting critical for security?
