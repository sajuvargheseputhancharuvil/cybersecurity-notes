# Module 3 – INTRODUCTION TO NETWORKING  
## 3.4 Proxies – Forward, Reverse & Transparent (CDSA-Focused Notes)

A proxy is a device or service that sits between two communicating parties and acts as a mediator.

**Key concept:** A true proxy must be able to inspect and mediate traffic.  
If it only forwards traffic without inspecting it, it behaves more like a gateway.

Most proxies operate at **Layer 7 (Application Layer)** of the OSI model.

---

## 1. What a Proxy Is (and Is Not)

**Common misconceptions:**
- Changing IP address ≠ always a proxy  
- VPN ≠ proxy (VPN operates at lower layers, not application mediation)  
- Gateway ≠ proxy (no inspection capability)  

A proxy:
- Intercepts traffic  
- Inspects it  
- Makes decisions  
- Forwards or blocks it  

Think of it as:

> An intelligent middleman that understands the application protocol.

---

## 2. Main Types of Proxies

There are three primary types you should understand:
1. Forward Proxy  
2. Reverse Proxy  
3. Transparent vs Non-Transparent Proxy  

---

## 3. Forward Proxy (Dedicated Proxy)

A Forward Proxy handles outgoing client requests.

**Flow:**
Client → Proxy → Internet

### How It Works
- Client sends request to proxy  
- Proxy inspects traffic  
- Proxy forwards request to destination  
- Response returns via proxy  

**Used commonly in:**
- Corporate networks  
- Web filtering environments  
- Malware defense environments  

### Security Benefits

Forward proxies:
- Block malicious domains  
- Inspect HTTP traffic  
- Enforce acceptable-use policies  
- Detect C2 traffic  

In corporate environments:
- Systems may not have direct internet access  
- All traffic must pass through proxy  

This creates a powerful defense layer.

### Malware & Proxy Awareness (Defensive Insight)

If malware:
- Uses native Windows APIs (WinSock) → likely proxy-aware  
- Uses non-native libraries → may bypass proxy unintentionally  

**Defensive takeaway:**

Proxy enforcement significantly disrupts basic malware communication.

Alternative malware channels:
- DNS tunneling  
- Non-HTTP C2 channels  

If DNS is monitored (e.g., Sysmon logging), detection improves significantly.

---

## 4. Reverse Proxy

A Reverse Proxy handles incoming requests.

**Flow:**
Internet → Reverse Proxy → Internal Server

### Purpose

Instead of protecting clients,  
reverse proxies protect servers.

They:
- Sit in front of web servers  
- Filter incoming traffic  
- Hide backend infrastructure  
- Absorb DDoS attacks  

### Common Uses
- Load balancing  
- DDoS protection  
- Web Application Firewall (WAF)  
- TLS termination  
- Backend server isolation  

Examples:
- Cloud-based reverse proxy services  
- Web Application Firewalls  

### Security Benefits

Reverse proxies:
- Hide internal IP addresses  
- Block malicious HTTP requests  
- Enforce rate limiting  
- Filter exploit payloads  

They reduce direct exposure of backend servers.

### Attacker Perspective

Reverse proxies are often used during:
- Post-exploitation pivoting  
- Tunneling through compromised systems  
- Firewall bypassing  

Example scenario:  
An attacker tunnels traffic through SSH and uses reverse-proxy behavior to evade IDS monitoring.

---

## 5. Transparent vs Non-Transparent Proxies

This refers to visibility from the client’s perspective.

### Transparent Proxy

Client does **not** know proxy exists:
- No configuration required  
- Proxy intercepts traffic automatically  
- Often implemented at gateway level  

**Used in:**
- ISPs  
- Schools  
- Corporate web filtering  

**Security implication:**  
User cannot easily bypass without advanced techniques.

---

### Non-Transparent Proxy

Client must be configured manually:
- Proxy address must be specified  
- Browser/system proxy settings required  
- If misconfigured → no internet access  

**Used in:**
- Corporate networks  
- Security testing environments  

---

## 6. Forward vs Reverse Proxy – Quick Comparison

| Feature       | Forward Proxy        | Reverse Proxy           |
|---------------|----------------------|--------------------------|
| Protects      | Clients              | Servers                  |
| Direction     | Outbound             | Inbound                  |
| Used for      | Web filtering        | WAF / Load balancing     |
| Client aware? | Usually yes          | No                       |
| Hides         | Internal users       | Backend servers          |

---

## 7. Where Proxies Sit in Network Security

In a secure architecture:

Internet → Reverse Proxy / WAF → Firewall → Internal Network  
Internal Clients → Forward Proxy → Internet  

**Layered security model:**
- Firewall filters network-level traffic  
- Proxy filters application-level traffic  
- IDS/IPS monitors behavior  

---

## 8. CDSA / Defensive Security Relevance

You must understand:
- How malware bypasses proxies  
- Why proxy logs are gold for investigation  
- How reverse proxies protect attack surface  
- Why split tunneling weakens proxy control  
- How DNS can bypass HTTP proxies  

---

## 9. Interview-Level Questions

1. Difference between forward and reverse proxy?  
2. Why does a proxy operate at Layer 7?  
3. How does a proxy improve malware defense?  
4. What is a transparent proxy?  
5. Why is a VPN not technically a proxy?  
