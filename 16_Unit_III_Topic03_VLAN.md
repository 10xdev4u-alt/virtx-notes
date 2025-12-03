---
title: "Unit III, Topic 03: VLAN (Virtual Local Area Network)"
id: unit3-topic3-vlan
tags:
  - unit3
  - network-virtualization
  - vlan
  - switching
  - 802.1q
aliases:
  - VLANs
  - Virtual LAN
links:
  - "[[00_Syllabus]]"
  - "[[15_Unit_III_Topic02_Tools_for_Network_Virtualization]]"
  - "[[17_Unit_III_Topic04_WAN_Architecture_and_SD-WAN]]"
---

# Unit III, Topic 03: VLAN (Virtual Local Area Network)

A **VLAN (Virtual Local Area Network)** is a fundamental network virtualization technology that allows you to segment a single physical Local Area Network (LAN) into multiple, logically separate LANs. Devices within a VLAN can communicate with each other as if they were on the same physical network segment, even if they are physically located on different floors, in different buildings, or connected to different switches.

## The Problem VLANs Solve: Broadcast Domains

In a traditional flat network, if one device sends a broadcast message (a message intended for all other devices on the network), it is sent to *every single port* on the switch. As a network grows, this broadcast traffic can become overwhelming, consuming bandwidth and CPU cycles on every connected device. This entire area of broadcast traffic is called a **broadcast domain**.

VLANs solve this by breaking a large broadcast domain into multiple smaller, isolated ones.

## How VLANs Work

### 1. Logical Segmentation
-   A network administrator can create multiple VLANs on a switch (e.g., VLAN 10 for Sales, VLAN 20 for Engineering, VLAN 30 for HR).
-   Each VLAN is its own isolated broadcast domain. Broadcast traffic from a device in VLAN 10 will only be sent to other devices in VLAN 10; it will not be seen by devices in VLAN 20 or 30.

### 2. Frame Tagging (IEEE 802.1Q)
-   To keep track of which traffic belongs to which VLAN, especially when traffic moves between switches, a process called **frame tagging** is used.
-   The **IEEE 802.1Q** standard defines how a small "tag" is inserted into the Ethernet frame header. This tag contains the **VLAN ID** (a number from 1 to 4094).
-   When a tagged frame arrives at a switch, the switch reads the VLAN ID and knows which VLAN the frame belongs to, ensuring it only forwards it to ports that are also part of that same VLAN.

### 3. Port Types
-   **Access Port:** An access port belongs to a single VLAN. Any device connected to an access port (like a user's PC) is automatically placed into that VLAN. Traffic leaving an access port is untagged.
-   **Trunk Port:** A trunk port is configured to carry traffic for **multiple VLANs** simultaneously between network devices (e.g., between two switches or between a switch and a router). It relies on 802.1Q tags to differentiate the traffic from the various VLANs.

### ASCII Diagram: VLAN Segmentation

```ascii
+-----------------------------------------------------------------+
|                            Switch 1                             |
|                                                                 |
|  Ports 1-4 [VLAN 10: Sales]      Ports 5-8 [VLAN 20: Engineering] |
|  +---------+  +---------+        +---------+  +---------+      |
|  | PC 1    |--| PC 2    |        | PC 3    |--| PC 4    |      |
|  +---------+  +---------+        +---------+  +---------+      |
|      ^                                 ^                        |
|      | Broadcast from PC 1           | Broadcast from PC 3      |
|      +-----> only goes to PC 2       +-----> only goes to PC 4  |
|                                                                 |
|                                      +-----------------------+  |
|                                      | Trunk Port (to Router)|  |
|                                      +-----------------------+  |
+-----------------------------------------------------------------+
```
In this diagram, PC 1 and PC 2 can communicate freely, but they cannot communicate directly with PC 3 or PC 4. For that, they would need to go through a router that connects the two VLANs.

## Key Advantages of VLANs

1.  **Enhanced Security:** By segmenting the network, you create isolation. The Sales department cannot "see" or access the servers in the Engineering department's VLAN without passing through a router or firewall where access control policies can be applied.
2.  **Improved Performance:** By creating smaller broadcast domains, you reduce the amount of unnecessary broadcast traffic on the network, freeing up bandwidth and improving overall performance.
3.  **Flexibility and Scalability:** A user can move their physical location (e.g., move desks from one floor to another) but remain in the same VLAN without any need for re-cabling or changing their IP address. The network administrator simply reconfigures the new switch port to the correct VLAN.
4.  **Cost Reduction:** VLANs allow you to logically segment the network without needing to buy physically separate switches for each department, making more efficient use of existing hardware.

> [!success] **Exam Focus**
> - **4-Mark Question:** "What is a VLAN and what are its primary advantages?"
>   - **Answer Strategy:** Define a VLAN as a technology that logically segments a physical LAN into multiple broadcast domains. Then, list and briefly explain its key advantages: 1) **Security** (isolation between segments), 2) **Performance** (reduced broadcast traffic), and 3) **Flexibility** (users can move physically but stay in the same logical network).
> - **2-Mark Question:** "What is the purpose of the IEEE 802.1Q standard?"
>   - **Answer:** The IEEE 802.1Q standard defines the process of **VLAN frame tagging**. It specifies how a VLAN ID is inserted into an Ethernet frame header so that network switches can identify which VLAN the traffic belongs to, which is essential for carrying traffic from multiple VLANs across a trunk link.
