# Complete Data Flow Example – End-to-End Communication

This section ties everything together by explaining what actually happens when a user types:

**`www.example.com`**

From a defensive analyst perspective:
- Every step leaves logs  
- Every layer can be attacked  
- Every device can enforce controls  

---

## 1. Step 1 – Connecting to Wi-Fi (WLAN Access)

Before anything else, the laptop must connect to the wireless network.

**What happens:**
1. Laptop scans for SSIDs  
2. User selects the correct network  
3. WPA2/WPA3 authentication occurs  
4. Secure wireless connection is established  

**Security Notes:**
- Weak Wi-Fi passwords enable unauthorized access  
- WPA2/WPA3 should be used (avoid WEP)  
- Rogue access points and evil twin attacks are common  

---

## 2. Step 2 – IP Assignment (DHCP)

If the laptop doesn’t already have an IP address, it performs the **DORA** process:
- Discover  
- Offer  
- Request  
- Acknowledge  

**Example configuration received:**
- IP: `192.168.1.10`  
- Subnet mask  
- Default gateway  
- DNS server  

The device can now communicate on the local network.

**Security Notes:**
- Rogue DHCP servers can push malicious gateways  
- DHCP logs are useful for investigations  
- `169.254.x.x` indicates DHCP failure (APIPA)  

---

## 3. Step 3 – DNS Resolution

User types: `www.example.com`  

The laptop must resolve the domain name to an IP address.

**DNS flow:**
1. Check local cache  
2. Query DNS server  
3. Receive response (e.g., `93.184.216.34`)  

**Security Notes:**
- DNS poisoning and spoofing are common attack techniques  
- DNS logs are valuable for threat hunting  
- Suspicious or newly registered domains are early indicators of compromise  

---

## 4. Step 4 – Data Encapsulation (Layer-by-Layer)

The request is prepared for transmission.

### Application Layer (Layer 7)
- Browser creates HTTP/HTTPS request  

### Transport Layer (Layer 4)
- TCP segment created  
- Source port: ephemeral port  
- Destination port: 80 (HTTP) or 443 (HTTPS)  

### Network Layer (Layer 3)
- Source IP: `192.168.1.10`  
- Destination IP: `93.184.216.34`  

### Data Link Layer (Layer 2)
- Frame created  
- Source MAC: Laptop  
- Destination MAC: Router  

If router MAC is unknown:
- ARP request is sent  

**Key Term:**  
**Encapsulation** = wrapping data with headers at each layer.

---

## 5. Step 5 – NAT at the Router

The router receives the packet.

Since the source IP is private, NAT occurs:

`192.168.1.10 → 203.0.113.45`

Example NAT table entry:

`203.0.113.45:4444 ↔ 192.168.1.10:5555`

The packet is forwarded to the ISP.

**Security Notes:**
- NAT hides internal addressing  
- Port forwarding can expose internal systems  
- NAT logs are critical for forensic correlation  

---

## 6. Step 6 – Internet Routing

The packet traverses multiple routers.

Each router:
- Reads the destination IP  
- Forwards to the next hop  

Eventually, the packet reaches the web server.

---

## 7. Step 7 – Server Processing

The server receives the packet.

Controls involved:
- Firewall checks whether ports 80/443 are allowed  
- Web server (Apache/Nginx/IIS) processes the request  
- Response is generated (HTML, CSS, JS)  

Response packet:
- Source: `93.184.216.34`  
- Destination: `203.0.113.45`  

---

## 8. Step 8 – NAT Reverse Translation

The router receives the response.

Using the NAT table:
`203.0.113.45 → 192.168.1.10`

The packet is forwarded to the laptop.

---

## 9. Step 9 – Decapsulation

The laptop receives the frame and removes:
- Data Link header  
- IP header  
- TCP header  

The browser processes the application data and renders the page.

---

## 10. Full Flow Summary

1. Connect to Wi-Fi  
2. Obtain IP via DHCP  
3. Resolve domain via DNS  
4. Create HTTP request  
5. Encapsulate packet  
6. ARP for router MAC  
7. NAT translation  
8. Route across the internet  
9. Server processes request  
10. Response returns  
11. NAT reverse translation  
12. Decapsulation and rendering  

---

## 11. Where Attacks Can Occur

| Step       | Possible Attack                  |
|------------|----------------------------------|
| Wi-Fi      | Evil twin, deauthentication      |
| DHCP       | Rogue DHCP                       |
| DNS        | Spoofing, tunneling              |
| Transport  | SYN flood                        |
| NAT        | Exposed port forwarding          |
| Server     | Web exploitation                 |
| Return     | Man-in-the-middle                |

This end-to-end view is critical for incident response.

---

## 12. Defensive Analyst Perspective

At each stage, logs may exist:
- DHCP logs  
- DNS logs  
- Firewall logs  
- NAT logs  
- Web server logs  
- IDS/IPS alerts  

**Key skill:**  
Correlation across layers is what turns alerts into real investigations.

---

## 13. Interview Questions to Master

1. Explain the complete web request flow  
2. Where does NAT occur?  
3. At what layer does ARP operate?  
4. What is encapsulation?  
5. Where can an IDS be placed in this flow?  
6. What logs would you review during an investigation? 
