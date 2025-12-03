---
title: "FAT02 - CS22051 Virtualization Techniques (2k25) - Answer Key"
id: virtx-fat02-2k25-anx
tags:
  - fat-answers
  - virtualization
  - unit2
  - unit3
  - unit4
aliases:
  - FAT02 2k25 Answers
links:
  - "[[virt_fat02_2k25]]"
---

# FAT02 - CS22051 Virtualization Techniques (2k25) - Answer Key

Here are the detailed answers for the Second Assessment Test (FAT) of the 2k25 series on Virtualization Techniques.

---

## PART A (10 x 2 = 20 Marks)

**1. Define virtual server consolidation.**

Virtual server consolidation is the process of migrating multiple workloads from many underutilized physical servers to run as virtual machines on a smaller number of more powerful, efficiently utilized physical servers. The primary goal is to increase hardware utilization and reduce the physical server footprint.

**2. Name any two benefits of virtual server consolidation.**

1.  **Reduced Costs:** Significant savings on hardware procurement, power, cooling, and data center space.
2.  **Simplified Management:** Fewer physical servers to manage, patch, and maintain.

**3. What is a key factor to consider when selecting a server virtualization platform?**

A key factor is the **total cost of ownership (TCO)**, which includes not just the initial software licensing costs, but also hardware requirements, ongoing support contracts, and the existing skillset of the IT staff. Other key factors include the platform's feature set (e.g., HA, live migration) and its ecosystem.

**4. Differentiate between persistent and non-persistent desktop virtualization?**

-   **Persistent VDI:** Each user is assigned a unique, dedicated virtual desktop. All user changes, installed applications, and data are **saved** and persist across sessions. It's like a personal physical desktop.
-   **Non-Persistent VDI:** Users are assigned a generic, fresh VM from a pool each time they log in. All changes are **discarded** upon logout, and the VM reverts to its original state.

**5. What role does a hypervisor play in desktop virtualization?**

In server-side desktop virtualization (like VDI), the hypervisor (typically Type-1) runs on the data center servers and is responsible for **creating, running, and managing the desktop virtual machines** that users connect to remotely. It partitions the server hardware and allocates resources to each desktop VM.

**6. List any four techniques that can be used to allow different virtual networks to coexist on the same physical infrastructure.**

These are primarily network overlay technologies:
1.  **VLAN (Virtual LAN):** Uses 802.1Q tagging to segment traffic at Layer 2.
2.  **VXLAN (Virtual Extensible LAN):** Encapsulates L2 frames in L3 UDP packets.
3.  **NVGRE (Network Virtualization using Generic Routing Encapsulation):** Another L2-over-L3 encapsulation protocol.
4.  **Geneve (Generic Network Virtualization Encapsulation):** A flexible encapsulation protocol designed to be extensible.

**7. Specify the primary purpose of cloud management platform(CMPs)in network virtualization. List some of the CMPs.**

**Primary Purpose:** The primary purpose of a Cloud Management Platform (CMP) in network virtualization is to provide a unified management and orchestration layer. It allows administrators to define, deploy, manage, and automate virtual networks and their associated services through a single interface, abstracting the complexity of the underlying infrastructure.

**List of CMPs:**
- OpenStack
- VMware vRealize Automation
- CloudStack
- Microsoft System Center

**8. Summarize the advantages of network virtualization with example.**

The main advantage of network virtualization is **agility**. For example, instead of physically cabling and manually configuring a new network segment for a new application (which could take days), an administrator can use software to provision a new, isolated virtual network with its own virtual switches and routers in minutes. Other advantages include reduced costs and enhanced security.

**9. Mention the use of VLANs in network virtualization.**

VLANs are a fundamental form of network virtualization used for **network segmentation**. They logically divide a single physical LAN into multiple, isolated broadcast domains. This is used to improve security by separating different departments (e.g., Sales and Engineering) and to improve performance by reducing broadcast traffic.

**10. Compare WAN with LAN in terms of connectivity.**

-   **LAN (Local Area Network):** Provides connectivity within a limited, local geographical area, such as a single office building, school, or home. It typically uses high-speed technologies like Ethernet.
-   **WAN (Wide Area Network):** Provides connectivity over a large geographical area, connecting multiple LANs together across cities, countries, or continents. It uses technologies like MPLS or the internet.

---

## PART B (3 x 10 = 30 Marks)

**11. (a) Evaluate a case study where a company implemented network virtualization to improve network scalability and efficiency. Analyze the impact of network virtualization on network management and performance.**

**Case Study: "CloudServe Inc."**

**Scenario:**
CloudServe Inc. is a rapidly growing cloud provider. They were using a traditional, VLAN-based network architecture in their data center. As they added more customers (tenants), they faced two major problems:
1.  **Scalability Limit:** They were approaching the 4,094 VLAN limit, which restricted their ability to onboard new, isolated customers.
2.  **Management Inefficiency:** Provisioning a new tenant's network required manual configuration of VLANs and access control lists (ACLs) across multiple physical switches, a process that was slow and error-prone.

**Implementation:**
CloudServe decided to implement a network virtualization solution using **VMware NSX**, which leverages the **VXLAN** overlay protocol.

**Impact on Network Scalability and Efficiency:**
-   **Massive Scalability:** By using VXLAN, they overcame the VLAN limit. VXLAN's 24-bit identifier allowed them to create up to 16 million logical network segments, giving them virtually limitless ability to scale and onboard new tenants.
-   **Hardware Efficiency:** They could now create these logical networks on top of their existing physical network (the "underlay") without needing to purchase new switches. The physical network was simplified to just provide basic IP connectivity.

**Analysis of Impact on Network Management and Performance:**

**Network Management:**
-   **Centralized Control:** Management was transformed. Instead of configuring individual switches, administrators could now define and manage all virtual networks, routers, and firewalls from the central NSX controller.
-   **Rapid Provisioning (Agility):** Provisioning a new, complex network for a customer became an automated, software-defined process that took minutes instead of days. This drastically improved their business agility.
-   **Simplified Troubleshooting:** The centralized controller provided a holistic view of the entire virtual network, making it easier to trace traffic flows and troubleshoot connectivity issues.

**Network Performance:**
-   **Micro-segmentation:** NSX allowed them to implement "zero-trust" security policies. They could create firewall rules that restricted traffic between individual VMs, even on the same logical network. This dramatically improved security by limiting the lateral movement of any potential threat.
-   **Performance Overhead:** A potential negative impact was the slight performance overhead from the VXLAN encapsulation/decapsulation process. However, they mitigated this by using modern servers with NICs that support VXLAN offloading, where the network card handles the encapsulation, freeing up CPU cycles.

**Conclusion:**
The implementation of network virtualization was highly successful. It solved their critical scalability issues, made network management far more efficient and automated, and significantly enhanced their security posture through micro-segmentation, enabling them to grow their business effectively.

**(OR)**

**11. (b) Apply the concepts of WAN architecture and WAN virtualization to a real-world scenario involving the optimization of wide-area network resources. Analyze the benefits and challenges of WAN virtualization in this context.**

**Real-World Scenario: "Global Retail Corp"**

Global Retail Corp has 200 branch stores, a corporate headquarters (HQ), and is increasingly using cloud-based applications like Office 365 and a cloud-hosted inventory system.

**Traditional WAN Architecture:**
Each of the 200 stores is connected back to the HQ data center via a single, expensive, and low-bandwidth **MPLS** circuit. All internet and cloud traffic from the stores is "backhauled" to the HQ to go through a central security firewall before reaching its destination.

**Problems:**
-   **High Cost:** The MPLS contracts for 200 stores are extremely expensive.
-   **Poor Performance:** Backhauling cloud traffic to HQ adds significant latency. Accessing Office 365 from a branch store is slow and unreliable.
-   **Low Agility:** Opening a new store is delayed by the weeks or months it takes the carrier to provision a new MPLS circuit.

**Applying WAN Virtualization (SD-WAN):**

Global Retail implements an SD-WAN solution. Each store gets a small SD-WAN appliance that can connect to both their existing MPLS link and a new, cheap local broadband internet link.

**Analysis of Benefits:**

1.  **Traffic Optimization & Performance:** SD-WAN's **application-aware routing** provides immediate benefits.
    -   Critical, internal traffic (like payment processing) is routed over the reliable MPLS link.
    -   Cloud traffic (Office 365) is sent directly out the local broadband internet connection, eliminating the backhaul latency and dramatically improving user experience.
    -   Guest Wi-Fi traffic is also sent over the broadband link, keeping it off the corporate network.
2.  **Cost Efficiency:** The company can now reduce the bandwidth of its expensive MPLS circuits (or eliminate them entirely at some stores) and rely more on the cheaper broadband links, leading to massive cost savings.
3.  **Increased Agility:** When a new store opens, they simply ship an SD-WAN appliance there, plug it into a standard internet connection, and it automatically downloads its configuration from the central controller (**zero-touch provisioning**). The store is online in minutes.
4.  **Centralized Management:** The IT team can monitor and manage the network for all 200 stores from a single web-based dashboard, pushing policy changes instantly.

**Analysis of Challenges:**

1.  **Security:** Enabling direct internet access from 200 branch stores creates 200 new points of entry for threats. This challenge is addressed by choosing an SD-WAN solution with an integrated firewall or by subscribing to a cloud-based security service (a model known as SASE - Secure Access Service Edge).
2.  **Complexity of Initial Policy Design:** While management is simpler long-term, the initial setup requires careful planning to define the application routing policies correctly.
3.  **Reliance on Public Internet:** The performance of the broadband links is not guaranteed like MPLS. The SD-WAN solution must be able to detect link degradation or outages and automatically failover traffic to the MPLS link or a secondary link (like 4G LTE).

**12. (a) How do network virtualization tools, including virtual switches, routers, SDN, and NFV, enhance flexibility, scalability, and resource management by abstracting physical hardware in modern networks? In what ways do these tools improve traffic management and adaptability, including features such as dynamic bandwidth allocation, QoS controls, real-time traffic analytics, and automated load balancing? What challenges do organizations encounter regarding interoperability issues, performance overhead, complex configuration management, security risks, and resource contention? What tools and techniques can be utilized to overcome these challenges?**

This is a comprehensive question covering the breadth of network virtualization.

**Enhancing Flexibility, Scalability, and Resource Management:**

Network virtualization tools abstract physical hardware, creating a flexible, software-defined overlay.
-   **Flexibility:** Virtual switches and routers can be created, configured, and connected programmatically in minutes, allowing network topologies to be designed and modified on the fly without touching physical cables.
-   **Scalability:** SDN controllers can manage thousands of physical and virtual devices from a central point. Overlay technologies like VXLAN break the 4094 VLAN limit, allowing for millions of logical network segments, essential for cloud-scale operations.
-   **Resource Management:** NFV allows network functions (firewalls, load balancers) to run as VMs, which can be scaled up or down by allocating more or fewer CPU/RAM resources, optimizing hardware use compared to fixed-capacity physical appliances.

**Improving Traffic Management and Adaptability:**

-   **Dynamic Bandwidth Allocation & QoS:** SDN controllers have a global view of the network. They can implement Quality of Service (QoS) policies to prioritize critical traffic (like VoIP) and dynamically allocate bandwidth to applications based on real-time needs.
-   **Real-time Traffic Analytics:** The centralized controller is a natural point for collecting telemetry and analytics, providing deep insight into traffic flows and network health, enabling faster troubleshooting.
-   **Automated Load Balancing:** SDN can automatically redirect traffic to avoid congested links. NFV allows virtual load balancers to be spun up on demand and integrated into the traffic flow programmatically to distribute application load.

**Challenges and Mitigation:**

1.  **Interoperability Issues:**
    -   **Challenge:** Hardware from different vendors may not uniformly support the protocols (like OpenFlow) used by an SDN controller.
    -   **Mitigation:** Use widely adopted standards. Employ overlay technologies (like VXLAN) that are hardware-agnostic, or choose a single-vendor ecosystem (like VMware NSX) for guaranteed compatibility.

2.  **Performance Overhead:**
    -   **Challenge:** The encapsulation/decapsulation of overlay protocols (VXLAN) and the software-based processing of packets can add latency and consume CPU cycles.
    -   **Mitigation:** Use hardware that supports overlay offloading (where the NIC handles encapsulation). Employ high-performance servers and ensure the SDN controller is not a bottleneck.

3.  **Complex Configuration Management:**
    -   **Challenge:** While powerful, managing a programmable network requires new skills in automation, scripting, and API integration, which can be more complex than traditional CLI management.
    -   **Mitigation:** Invest heavily in staff training. Utilize Cloud Management Platforms (CMPs) and automation tools (like Ansible, Puppet) to manage configurations declaratively and reduce manual error.

4.  **Security Risks:**
    -   **Challenge:** The centralized SDN controller becomes a critical target. If compromised, the entire network is at risk.
    -   **Mitigation:** Secure the controller with robust access controls, encryption, and redundancy. Implement micro-segmentation to contain threats, limiting lateral movement even if a part of the network is breached.

5.  **Resource Contention:**
    -   **Challenge:** VNFs running on a server compete for CPU, memory, and I/O, just like regular VMs. A "noisy neighbor" VNF can impact the performance of others.
    -   **Mitigation:** Use hypervisor resource management features (reservations, limits, shares) to guarantee resources for critical VNFs. Monitor performance closely to balance workloads.

**(OR)**

**12. (b) How does VLAN technology enhance network segmentation in smart farming and precision agriculture without requiring additional hardware? In what ways does it improve security by isolating functions such as monitoring systems and irrigation control, and how does it facilitate traffic management within agricultural organizations? Additionally, what are the positive and negative impacts of VLANS on network performance and remote monitoring, as well as the challenges of configuring and troubleshooting in large-scale operations?**

**VLANs in Smart Farming:**

In a smart farm, numerous IoT devices and systems are connected to a single physical network infrastructure. VLANs are a perfect technology to logically segment this network without needing to run separate physical cables for each system.

**Enhancing Segmentation and Security:**
A farm can create multiple VLANs on its existing switches to isolate different functions:
-   **VLAN 10 (Sensor Network):** For soil moisture sensors, temperature sensors, and weather stations.
-   **VLAN 20 (Control Systems):** For critical irrigation controllers, automated feeders, and drone controls.
-   **VLAN 30 (Monitoring & Data):** For security cameras and data servers.
-   **VLAN 40 (Guest/Office Wi-Fi):** For general office and visitor use.

This segmentation provides **security through isolation**. Traffic on the Sensor Network (VLAN 10) cannot directly access the critical Control Systems (VLAN 20). A security breach on the guest Wi-Fi (VLAN 40) would be contained and could not be used to tamper with the irrigation system. All inter-VLAN communication must pass through a router or firewall, where strict access rules can be enforced.

**Facilitating Traffic Management:**
By breaking the farm's network into smaller broadcast domains, VLANs prevent broadcast storms from one system (e.g., a faulty sensor) from flooding the entire network and disrupting other critical operations. This improves overall network stability. QoS policies can also be applied at the router on a per-VLAN basis, prioritizing traffic from the Control Systems VLAN over less critical data.

**Impacts on Performance and Remote Monitoring:**
-   **Positive Impact:** Performance is improved by reducing unnecessary broadcast traffic. For remote monitoring, VLANs enhance security by ensuring that remote access (e.g., via a VPN) can be restricted to only the necessary VLAN (e.g., a user can be given access to the Monitoring VLAN but not the Control VLAN).
-   **Negative Impact:** Inter-VLAN communication introduces a slight latency as traffic must be routed. If not properly configured, the router between VLANs can become a bottleneck.

**Challenges in Large-Scale Operations:**
-   **Configuration Complexity:** In a large-scale farm with hundreds of devices and multiple switches, managing VLAN assignments, trunk links, and router configurations can become complex and prone to error.
-   **Troubleshooting:** When a device can't communicate, troubleshooting becomes more difficult as the issue could be a physical connection, an incorrect IP address, or a VLAN misconfiguration on a switch port or trunk link. This requires a higher level of networking expertise.

**13. (a) A small company, TechZone, has several storage devices from different brands. As the amount of data grows, the IT team finds it hard to manage all the storage separately. They want a solution that allows them to combine all their storage into one system so they can manage it more easily and make better use of space. The IT manager suggests using storage virtualization to solve the problem.**

**Solution using Storage Virtualization:**

The IT manager's suggestion to use storage virtualization is the correct approach to solve TechZone's problem.

**How Storage Virtualization Solves the Problem:**
Storage virtualization introduces a software or hardware layer that **abstracts** the physical storage devices from the servers that use them. This layer **pools** the capacity from all the heterogeneous storage devices (from different brands) into a single, unified virtual storage pool.

**Benefits for TechZone:**

1.  **Centralized Management:** Instead of logging into multiple different management interfaces for each brand of storage, the IT team can now manage the entire storage pool from a **single, centralized console**. This dramatically simplifies tasks like provisioning new storage, monitoring capacity, and managing permissions.
2.  **Improved Space Utilization:** By pooling all the storage, the company can make much better use of its total capacity. Pockets of stranded, unused space on different devices are eliminated. Features like **thin provisioning** can be enabled at the virtualization layer, allowing them to allocate large virtual disks to servers that only consume physical space as data is actually written, further improving efficiency.
3.  **Seamless Data Migration:** When an old storage device needs to be replaced, the virtualization layer can migrate the data to a new device **non-disruptively** in the background. The servers and applications are completely unaware of this migration and experience no downtime.
4.  **Advanced Features:** The virtualization layer can provide advanced features like snapshots, replication, and storage tiering across all the underlying devices, even if the devices themselves don't support these features natively.

**Implementation:**
TechZone could implement this using a dedicated storage virtualization appliance that sits in front of their existing storage devices, or by using a software-defined storage (SDS) solution that runs on commodity servers.

**(OR)**

**13. (b) A company called BrightTech runs many programs on its computers at the same time. Sometimes, the computers become slow or stop working properly because they don't have enough physical memory (RAM). The IT technician suggests using memory virtualization to solve this problem and make better use of the memory.**

**Solution using Memory Virtualization:**

The IT technician's suggestion is correct. This scenario describes a virtualized environment where multiple virtual machines (representing the "many programs") are running on physical host computers. Memory virtualization, managed by the hypervisor, can solve this problem using several techniques.

**How Memory Virtualization Solves the Problem:**

1.  **Memory Overcommitment:**
    -   **Concept:** The hypervisor can allocate more total virtual RAM to all the VMs than the physical RAM that actually exists on the host.
    -   **How it helps BrightTech:** This allows BrightTech to run more programs (VMs) on their existing computers. It works because not all programs will use their maximum allocated memory at the same time. This technique increases the density of VMs per host, making better use of the hardware.

2.  **Transparent Page Sharing (TPS):**
    -   **Concept:** The hypervisor scans the memory of all running VMs to find identical memory pages. For example, if many VMs are running the same operating system, they will have many identical OS files in memory.
    -   **How it helps BrightTech:** TPS stores only one copy of these identical pages in physical RAM and shares it among all the VMs that need it. This memory deduplication frees up a significant amount of physical RAM, allowing more programs to run smoothly without the computer becoming slow.

3.  **Memory Ballooning:**
    -   **Concept:** This is a cooperative technique. When a host computer is running low on memory, the hypervisor activates a "balloon driver" inside a low-priority VM.
    -   **How it helps BrightTech:** The balloon driver requests memory from its own guest OS, causing that OS to page out its least important data to disk. This memory is then released back to the hypervisor, which can give it to another, more demanding program. This is a graceful way to reallocate memory without causing severe performance issues.

By using these techniques, memory virtualization allows BrightTech to run more programs efficiently on their existing hardware, solving the problem of computers becoming slow or crashing due to insufficient RAM.
