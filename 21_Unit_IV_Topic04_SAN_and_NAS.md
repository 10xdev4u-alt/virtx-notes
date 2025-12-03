---
title: "Unit IV, Topic 04: SAN and NAS"
id: unit4-topic4-san-nas
tags:
  - unit4
  - storage
  - san
  - nas
  - storage-networking
aliases:
  - Storage Area Network
  - Network Attached Storage
  - SAN vs. NAS
links:
  - "[[00_Syllabus]]"
  - "[[20_Unit_IV_Topic03_Risks_of_Storage_Virtualization]]"
  - "[[22_Unit_IV_Topic05_RAID]]"
---

# Unit IV, Topic 04: SAN and NAS

Storage Area Networks (SAN) and Network Attached Storage (NAS) are the two dominant methods for providing centralized storage on a network. They operate fundamentally differently and are designed for different use cases. Understanding their differences is critical.

## 4.3 SAN (Storage Area Network)

A **Storage Area Network (SAN)** is a dedicated, high-speed network that interconnects and presents shared pools of **block-level** storage to servers.

From the server's perspective, the storage provided by a SAN appears as a locally attached raw disk (a logical unit or LUN), which the server's operating system can then partition and format with its own file system (like NTFS or ext4).

### Key Characteristics of a SAN
1.  **Block-Level Access:** Servers access storage as raw data blocks. This is the key differentiator and is ideal for high-performance, transactional applications.
2.  **Dedicated Network:** A SAN uses its own separate network, isolated from regular user LAN traffic. This ensures high, predictable performance. The most common SAN protocols are:
    -   **Fibre Channel (FC):** A very high-speed protocol designed specifically for storage. It is the gold standard for performance but is also expensive and complex.
    -   **iSCSI (Internet Small Computer System Interface):** This protocol encapsulates SCSI storage commands into TCP/IP packets, allowing SANs to run over standard Ethernet networks. It is more cost-effective and easier to manage than Fibre Channel.
3.  **High Performance:** Designed for very high I/O throughput and low latency, making it suitable for the most demanding enterprise applications.
4.  **High Scalability:** Can scale to support hundreds of servers and petabytes of storage.

### ASCII Diagram: Simplified SAN Architecture
```ascii
+-----------------------------------------------------------+
|                          SERVERS                          |
|  (Each with a Host Bus Adapter - HBA)                     |
| +-----------+ +-----------+ +-----------+               |
| |  Server A | |  Server B | |  Server C |               |
| +-----------+ +-----------+ +-----------+               |
|       |           |           |                           |
+-------|-----------|-----------|---------------------------+
        |           |           |
+-------+-----------+-----------+---------------------------+
|                  DEDICATED SAN FABRIC                     |
|              (Fibre Channel or iSCSI Switches)            |
+-------+-----------+-----------+---------------------------+
        |           |           |
+-------|-----------|-----------|---------------------------+
|       |           |           |                           |
| +-----------+ +-----------+ +-----------+               |
| | Storage   | | Storage   | | Storage   |               |
| | Array 1   | | Array 2   | | Array 3   |               |
| +-----------+ +-----------+ +-----------+               |
|                  (Block-Level Storage Pool)               |
+-----------------------------------------------------------+
```

## 4.4 NAS (Network Attached Storage)

A **Network Attached Storage (NAS)** device is a self-contained storage server connected to a standard LAN that provides centralized **file-level** data access to clients.

A NAS device runs its own operating system and manages its own file system. It presents this storage to clients on the network as a shared folder (or "share").

### Key Characteristics of a NAS
1.  **File-Level Access:** Clients access data as files and folders using standard network protocols like **NFS (Network File System)** for Linux/Unix clients or **SMB/CIFS (Server Message Block/Common Internet File System)** for Windows clients.
2.  **Uses Shared LAN:** A NAS connects to and uses the existing local area network (LAN). It shares bandwidth with regular user traffic, which can be a performance consideration.
3.  **Ease of Use:** Generally much simpler to deploy and manage than a SAN. It's often a "plug-and-play" device.
4.  **Cost-Effective:** Typically more affordable than a SAN, making it very popular for small-to-medium businesses (SMBs) and home users.

### ASCII Diagram: Simplified NAS Architecture
```ascii
+---------------------------------------------------------------+
|                            CLIENTS                            |
|             (Desktops, Laptops, Servers on LAN)               |
| +---------+ +---------+ +---------+                         |
| | Client A| | Client B| | Client C|                         |
| +---------+ +---------+ +---------+                         |
|       |         |         |                                   |
+-------|---------|---------|-----------------------------------+
        |         |         |
+-------+---------+---------+-----------------------------------+
|                     SHARED LAN (Ethernet)                     |
+-------------------------+-------------------------------------+
                          |
            +-------------+-------------+
            |      NAS Device             |
            | (Self-contained appliance)  |
            | +-------+    +----------+ |
            | |  OS   |----| File Sys | |
            | +-------+    +----------+ |
            | |        DISK STORAGE     | |
            +-----------------------------+
```

## Summary: SAN vs. NAS

This comparison is a classic exam topic.

| Feature        | SAN (Storage Area Network)                             | NAS (Network Attached Storage)                         |
|----------------|--------------------------------------------------------|--------------------------------------------------------|
| **Access Level** | **Block-level**                                        | **File-level**                                         |
| **Protocols**  | Fibre Channel, iSCSI                                   | NFS, SMB/CIFS                                          |
| **Network**    | Dedicated, separate network (the "SAN")                | Shared, existing LAN                                   |
| **Performance**| High throughput, low latency                           | Lower than SAN, dependent on LAN traffic               |
| **Management** | Complex (LUNs, zoning, HBAs)                           | Simple (Shares, permissions)                           |
| **Cost**       | High                                                   | Low to Medium                                          |
| **Best For**   | Databases, virtual machine OS disks, high-performance applications | Centralized file sharing, user home directories, backups, unstructured data |

> [!success] **Exam Focus**
> - **8-Mark Question:** "Compare and contrast SAN and NAS technologies."
>   - **Answer Strategy:** This is a core question. Use a table like the one above to structure your answer. For each feature (Access Level, Protocols, etc.), clearly state the difference between SAN and NAS. Conclude by summarizing their ideal use cases to show you understand their practical application.
> - **2-Mark Question:** "What is the primary difference between how a server accesses storage on a SAN versus a NAS?"
>   - **Answer:** On a SAN, a server accesses storage at the **block level**, seeing it as a raw disk that it must format. On a NAS, a server accesses storage at the **file level**, seeing it as a pre-formatted network share.
