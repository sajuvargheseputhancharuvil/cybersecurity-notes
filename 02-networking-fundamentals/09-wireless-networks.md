# Wireless Networks

Wireless networking enables devices to communicate using radio waves instead of physical cables.

It provides:
- Mobility  
- Flexibility  
- Rapid deployment  

**Defensive security perspective:**  
Wireless networks extend the attack surface beyond physical boundaries.  
Unlike wired networks, attackers do not need physical access to connect or intercept traffic.

---

## 1. What is a Wireless Network?

A wireless network connects devices using radio signals.

**Devices supported:**
- Laptops  
- Smartphones  
- IoT devices  
- Tablets  
- Smart TVs  

**Used for:**
- Internet access  
- File sharing  
- Application access  

### Advantages vs Disadvantages

| Advantage         | Explanation                          |
|-------------------|--------------------------------------|
| Mobility          | Move freely within coverage area     |
| Easy Installation | No cabling required                  |
| Scalability       | Easy to add new devices              |

| Disadvantage   | Explanation                               |
|----------------|-------------------------------------------|
| Interference   | Walls and electronics affect signals      |
| Security Risks | Easier to intercept than wired networks   |
| Speed Limits   | Usually slower than wired Ethernet        |

---

## 2. Wireless Router

A wireless router combines multiple functions:
- Router (Layer 3)  
- Switch (Layer 2)  
- Wireless Access Point (AP)  

### Components of a Wireless Router

| Component     | Purpose                         |
|---------------|----------------------------------|
| WAN Port      | Connects to ISP modem            |
| LAN Ports     | Wired local connections          |
| Antennae      | Transmit/receive Wi-Fi signals  |
| CPU & Memory  | Routing and network control     |

### Security Considerations

Common router misconfigurations:
- Default credentials not changed  
- WPS enabled  
- Weak Wi-Fi encryption  
- Outdated firmware  

**Compromised router = full traffic visibility for attacker.**

---

## 3. Mobile Hotspot

A mobile hotspot allows a smartphone to share its cellular data via Wi-Fi.

**Used when:**
- No available Wi-Fi  
- Traveling  
- Backup connectivity needed  

### How It Works
1. Phone connects to cellular network (4G/5G)  
2. Phone creates Wi-Fi access point  
3. Other devices connect to phone  

**Limitations:**
- Limited range  
- High battery drain  
- Dependent on cellular coverage  

### Security Risks
- Weak hotspot password  
- Public sharing of personal device  
- MITM risk if poorly configured  

---

## 4. Cellular Networks & Cell Towers

A cell tower provides wireless coverage in a defined geographic area (cell).

Phones connect to the nearest tower.  
As you move, devices perform handoff to the next tower.

### Cell Tower Structure
- Antennas  
- Radio transmitters/receivers  
- Base Station Controller (BSC)  
- Backhaul link (fiber or microwave)  

### Cell Types

| Type            | Coverage                    |
|-----------------|-----------------------------|
| Macro Cells     | Large coverage (rural)      |
| Micro/Small Cells | Urban dense environments |

### Security Considerations
- Fake base stations (IMSI catchers)  
- Signal interception  
- SIM swapping attacks  
- SS7 vulnerabilities (telecom signaling abuse)  

Cellular networks are more secure than open Wi-Fi, but not immune.

---

## 5. Wireless Frequencies

Wireless communication operates on radio frequencies measured in Hertz (Hz).

### Wi-Fi Frequency Bands

**2.4 GHz**
- Longer range  
- Better wall penetration  
- Slower speeds  
- More interference (Bluetooth, microwaves)  

**5 GHz**
- Faster speeds  
- Shorter range  
- Less interference  

### Cellular Bands
- 700 MHz (long range)  
- 2.6 GHz (mid-range)  
- 5G high bands (e.g., 28 GHz)  

### Frequency Comparison

| Frequency         | Range   | Speed  | Use Case            |
|-------------------|---------|--------|---------------------|
| Lower Frequency   | Longer  | Slower | Rural coverage      |
| Higher Frequency  | Shorter | Faster | Urban high-speed    |

### Security Relevance
- 2.4 GHz congestion → packet loss  
- 5 GHz more stable for enterprise  
- Rogue APs can operate on same frequencies  

---

## 6. Key Wireless Security Risks (CDSA Focus)

### 1. Eavesdropping
If encryption is weak, traffic can be sniffed.

### 2. Rogue Access Points
Attackers set up fake Wi-Fi networks (e.g., “Free Airport WiFi”).

### 3. Evil Twin Attack
Fake AP mimics legitimate SSID.

### 4. Weak Encryption
Avoid:
- WEP (broken)  
- WPA (weak)  

Use:
- WPA2 (minimum)  
- WPA3 (preferred)  

### 5. Deauthentication Attacks
Attackers force clients to disconnect.  
Often used to capture WPA handshakes.

---

## 7. Real-World Daily Wireless Usage

In one day, you likely use:
- Wi-Fi (home/office)  
- Cellular (4G/5G)  
- Hotspot (travel)  
- Bluetooth devices  

Each has:
- Different security model  
- Different risks  

---

## 8. Defensive Analyst Takeaways (CDSA Level)

- Wireless increases attack surface  
- Radio signals can be intercepted  
- Router configuration is critical  
- WPA3 preferred over older standards  
- Rogue AP detection is important  
- Cellular networks also have vulnerabilities  

---

## 9. Interview Questions to Prepare

1. Difference between 2.4 GHz and 5 GHz?  
2. What is a rogue access point?  
3. What security protocol should Wi-Fi use?  
4. How does a mobile hotspot work?  
5. What is a deauthentication attack?  
6. Why are wireless networks riskier than wired?
