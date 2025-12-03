---
title: "Unit III, Topic 04: WAN Architecture and SD-WAN"
id: unit3-topic4-wan-sdwan
tags:
  - unit3
  - network-virtualization
  - wan
  - sd-wan
aliases:
  - WAN Virtualization
  - SD-WAN
links:
  - "[[00_Syllabus]]"
  - "[[16_Unit_III_Topic03_VLAN]]"
  - "[[ClgMatx/SemVPrep/VirtX/Unit_03_Quiz]]"
---

# Unit III, Topic 04: WAN Architecture and WAN Virtualization (SD-WAN)

## 3.3.1 Traditional WAN Architecture

A **Wide Area Network (WAN)** is a network that connects geographically dispersed local area networks (LANs), such as linking a company's branch offices to its central data center.

For decades, the standard for building a reliable enterprise WAN was **MPLS (Multi-Protocol Label Switching)**. MPLS is a private, dedicated connection provided by a telecommunications carrier. It offers high reliability and predictable performance, but it comes with significant challenges.

### Challenges with Traditional WANs:
-   **High Cost:** MPLS circuits are extremely expensive compared to standard broadband internet.
-   **Limited Agility & Slow Deployment:** Getting a new MPLS circuit provisioned for a new branch office can take weeks or even months.
-   **Inefficient Traffic Routing:** In a traditional "hub-and-spoke" model, all traffic from a branch office—including traffic destined for the internet or a cloud service—is often "backhauled" to the central data center for security inspection. This creates a major performance bottleneck and adds latency for cloud applications.
-   **Management Complexity:** Managing different carriers and connection types across dozens or hundreds of sites is complex and time-consuming.

## 3.3.2 WAN Virtualization (Software-Defined WAN - SD-WAN)

As businesses moved to the cloud, the limitations of the traditional WAN became a major roadblock. **WAN Virtualization**, most commonly implemented as **Software-Defined WAN (SD-WAN)**, applies the principles of SDN to solve these challenges.

**SD-WAN** is a technology that abstracts the underlying WAN transport services (like MPLS, broadband internet, 4G/5G LTE) into a single, virtual overlay network that can be centrally managed and intelligently controlled.

### Key Characteristics and Advantages of SD-WAN

1.  **Transport Independence:**
    -   SD-WAN can use multiple types of network transport simultaneously (e.g., MPLS, broadband, LTE). It creates a single, logical pool of bandwidth from these diverse connections, abstracting the physical underlay.

2.  **Centralized Control and Management:**
    -   The entire WAN is managed from a single, centralized software controller. Network policies and configurations are created on the controller and pushed out to all branch office devices automatically. This drastically simplifies management and ensures policy consistency.

3.  **Application-Aware Routing (Intelligent Path Selection):**
    -   This is a key feature. The SD-WAN solution can identify application traffic (e.g., it can distinguish between VoIP, Office 365, and YouTube traffic).
    -   It can then intelligently route that traffic over the most appropriate path based on predefined policies and real-time network conditions. For example:
        -   **VoIP traffic (high priority):** Send over the reliable MPLS link.
        -   **Office 365 traffic (cloud app):** Send directly out the local broadband internet connection to avoid backhauling.
        -   **Guest Wi-Fi traffic (low priority):** Send over the cheapest best-effort broadband link.

4.  **Increased Agility and Zero-Touch Provisioning:**
    -   New branch offices can be brought online in minutes. An SD-WAN appliance is shipped to the site, plugged in, and it automatically downloads its configuration from the central controller. This is known as "zero-touch provisioning."

5.  **Significant Cost Savings:**
    -   By intelligently utilizing cheaper broadband internet connections, organizations can reduce their reliance on expensive MPLS circuits, leading to major cost savings.

### ASCII Diagram: SD-WAN Concept

```
+------------------------------------------------------------------------------+
|                         Central SD-WAN Controller (Cloud or On-Prem)         |
|                          (Policy, Orchestration, Analytics)                  |
+------------------------------------------------------------------------------+
        ^                                                              ^
        | (Control Plane: Policies are pushed to all sites)            |
        v                                                              v
+-----------------------+                            +-----------------------+
|    Branch Office 1    |                            |      Data Center      |
| +-------------------+ |                            | +-------------------+ |
| | SD-WAN Appliance  | |                            | | SD-WAN Appliance  | |
| +-------+-----+-----+ |                            | +-------+-----+-----+ |
|         |     |       |                            |         |     |       |
+---------|-----|-------+                            +---------|-----|-------+
          |     |                                              |     |
          |     +----------------------------------------------+     |
          (MPLS Link - For Critical Traffic)                         |
          +----------------------------------------------------------+
          (Broadband Internet - For Cloud/Internet Traffic)

<< VIRTUAL OVERLAY NETWORK >>
--------------------------------------------------------------------------------
<< PHYSICAL UNDERLAY NETWORK (MPLS, Internet, LTE, etc.) >>
```

> [!success] **Exam Focus**
> - **6-Mark Question:** "Describe the challenges of traditional WAN architectures and explain how SD-WAN addresses them."
>   - **Answer Strategy:** First, list the challenges of traditional WANs (High Cost, Low Agility, Inefficient Routing). Then, for each challenge, explain how a specific SD-WAN feature provides a solution. For High Cost, explain how SD-WAN uses cheaper broadband. For Low Agility, explain zero-touch provisioning. For Inefficient Routing, explain application-aware routing and direct internet breakout.
> - **4-Mark Question:** "What is application-aware routing in SD-WAN?"
>   - **Answer:** Explain that it is the ability of an SD-WAN solution to identify different types of application traffic (e.g., voice, video, cloud apps). Based on predefined policies, it then intelligently routes each application over the most optimal transport path (e.g., MPLS for voice, broadband for cloud apps) to ensure performance, reliability, and cost-efficiency.
