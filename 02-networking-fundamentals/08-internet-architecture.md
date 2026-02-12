# Internet Architecture

Internet architecture explains how systems are structured to communicate and deliver services.

Different architectures solve different problems:
- Scalability  
- Performance  
- Cost  
- Security  
- Manageability  

In real-world environments, hybrid combinations of these models are common.

**Defensive security perspective:**  
Architecture determines attack surface, trust boundaries, and failure impact.

---

## 1. Peer-to-Peer (P2P) Architecture

In P2P architecture, every node can act as:
- Client  
- Server  

There is no strict central authority in fully decentralized models.

### How It Works
Devices connect directly to each other and share:
- Files  
- Processing power  
- Bandwidth  

**Example:** Torrent-based file sharing

### Advantages

| Advantage        | Explanation                     |
|------------------|---------------------------------|
| Scalability      | More peers = more resources     |
| Resilience       | No single central server        |
| Cost Distribution| Resource load shared            |

### Disadvantages

| Disadvantage        | Explanation                          |
|---------------------|--------------------------------------|
| Hard to Manage      | No centralized control               |
| Reliability Issues  | If peers leave, resources disappear  |
| Security Risks      | Every node exposed                   |

### Security Considerations
- Malware distribution is common in P2P  
- Difficult to enforce security policies  
- Hard to monitor centrally  
- Used in botnet architectures  

**CDSA Insight:**  
P2P traffic may bypass traditional centralized inspection methods.

---

## 2. Client-Server Architecture

The most common architecture on the internet.

**Clients request → Servers respond**

**Examples:**
- Websites  
- Email services  
- Enterprise applications  

### How It Works
1. Browser sends request  
2. Web server processes request  
3. Server sends response  

### Advantages

| Advantage            | Explanation                    |
|---------------------|--------------------------------|
| Centralized Control | Easier updates and management  |
| Security Enforcement| Central policy control         |
| Optimized Performance | Dedicated server hardware   |

### Disadvantages

| Disadvantage           | Explanation                          |
|------------------------|--------------------------------------|
| Single Point of Failure| Server outage = service down         |
| Cost                   | Infrastructure expensive             |
| Network Congestion     | High traffic can overwhelm server    |

---

## 3. Tiered Client-Server Models

### Single-Tier
- Client, server, and database on the same machine  
- Rare in production  
- Used mostly for testing or small standalone applications  

### Two-Tier
- Client (presentation layer)  
- Database server (data layer)  

Common in desktop applications.

> Note: Typical web browsing is not pure two-tier because browsers do not directly communicate with databases.

### Three-Tier (Very Important)
1. Client (presentation layer)  
2. Application server (business logic)  
3. Database server (data layer)  

**Benefits:**
- Scalability  
- Better security segmentation  
- Easier maintenance  

### N-Tier Architecture
Extension of three-tier with:
- Load balancers  
- Multiple application servers  
- Caching layers  
- Microservices  

Common in:
- Large-scale web applications  
- Cloud environments  

### Security Perspective (Client-Server)
- Server compromise = major impact  
- Requires patch management  
- Needs segmentation between tiers  
- API endpoints increase exposure  

**CDSA Tip:**  
Proper segmentation between tiers limits lateral movement.

---

## 4. Hybrid Architecture

Combination of Client-Server and P2P.

Central server handles:
- Authentication  
- Coordination  

Peers handle:
- Direct data exchange  

**Example:** Video conferencing applications

### Advantages

| Advantage       | Explanation                                  |
|-----------------|----------------------------------------------|
| Efficient       | Reduces server load                          |
| Central Control | Authentication and coordination maintained   |

### Disadvantages

| Disadvantage        | Explanation                                   |
|---------------------|-----------------------------------------------|
| Complex Design      | Harder to implement                           |
| Central Dependency  | If central node fails, coordination stops     |

### Security Insight
- Central server compromise impacts trust model  
- Peer connections may bypass inspection tools  
- Harder to enforce consistent logging  

---

## 5. Cloud Architecture

Cloud architecture is hosted by providers such as:
- AWS  
- Azure  
- Google Cloud  

Users:
- Access services  
- Do not manage physical hardware  

### Core Characteristics

| Characteristic           | Meaning                         |
|--------------------------|----------------------------------|
| On-Demand Self-Service  | Automatic provisioning           |
| Broad Network Access    | Access via internet              |
| Resource Pooling        | Shared infrastructure            |
| Rapid Elasticity        | Scale up/down quickly            |
| Measured Service        | Pay per usage                    |

### Advantages
- High scalability  
- Reduced infrastructure management  
- Global accessibility  

### Disadvantages
- Vendor lock-in  
- Compliance concerns  
- Internet dependency  

### Security Considerations
- Shared responsibility model  
- Misconfigured cloud storage is a common breach cause  
- Identity and access management (IAM) is critical  
- API security is important  

**CDSA Insight:**  
Many modern breaches stem from cloud misconfigurations.

---

## 6. Software-Defined Networking (SDN)

Modern networking model that separates:
- Control Plane (decision-making)  
- Data Plane (packet forwarding)  

Traditional devices combine both planes.  
SDN introduces:
- Centralized controller  
- Programmable network  

### Advantages

| Advantage           | Explanation                 |
|---------------------|-----------------------------|
| Centralized Control | Simplifies management       |
| Automation          | Rapid policy changes        |
| Traffic Optimization| Dynamic routing             |

### Disadvantages

| Disadvantage      | Explanation                        |
|-------------------|------------------------------------|
| Controller Risk   | Single point of failure            |
| Complexity        | Requires new operational skills    |

### Security Impact
- Central controller is a high-value target  
- Compromise can affect the entire network  
- Strong access control and hardening required  

---

## 7. Architecture Comparison Summary

| Architecture   | Centralized         | Scalability | Management  | Common Use           |
|----------------|---------------------|-------------|-------------|----------------------|
| P2P            | No                  | High        | Complex     | File sharing         |
| Client-Server  | Yes                 | Moderate    | Easier      | Websites             |
| Hybrid         | Partial             | High        | Complex     | Messaging apps       |
| Cloud          | Provider-based      | High        | Outsourced  | SaaS                 |
| SDN            | Control centralized | High        | Specialized | Enterprise networks  |

---

## 8. Defensive Analyst Takeaways (CDSA Level)

- Architecture determines attack surface  
- Centralized models are easier to monitor  
- P2P architectures are harder to control  
- Hybrid architectures increase complexity  
- Cloud environments require strong IAM and logging  
- SDN controllers are critical assets  

---

## 9. Interview Questions to Prepare

1. Difference between P2P and Client-Server?  
2. What is three-tier architecture?  
3. What are the benefits of cloud architecture?  
4. What is SDN?  
5. What is a single point of failure?  
6. Why is architecture important in security design? 
