---
title: "Unit IV: SAN, NAS, and RAID"
id: unit4-san-nas-raid
tags: [virtualization, storage, san, nas, raid, storage-networking, unit4]
aliases: [Storage Area Network, Network Attached Storage, Redundant Array of Independent Disks]
links: ["[[00_Syllabus]]", "[[13_Unit_IV_Types_of_Storage_Virtualization]]"]
---

# Unit IV: SAN, NAS, and RAID

Having explored the concepts of storage virtualization, let's now look at the core underlying technologies that provide the physical and logical storage infrastructure for virtualized environments: **SAN, NAS, and RAID**.

## 4.3 SAN (Storage Area Network)

A **Storage Area Network (SAN)** is a dedicated, high-speed network that provides access to consolidated, block-level storage. It makes storage devices (like disk arrays) appear to servers as locally attached drives, even though they might be physically distant.

### Key Characteristics of a SAN

1.  **Block-Level Access:** Servers access storage at the block level, which is the same way they would access a local hard drive. This is ideal for high-performance applications like databases and operating systems.
2.  **Dedicated Network:** A SAN typically uses a separate, dedicated network (often Fibre Channel or iSCSI) to move storage traffic, keeping it off the main LAN.
3.  **Scalability:** Easily scalable by adding more storage devices or servers to the SAN.
4.  **High Performance:** Designed for very high I/O throughput and low latency.
5.  **Centralized Management:** Storage is managed centrally, simplifying provisioning and maintenance.

### Technologies within a SAN

*   **Fibre Channel (FC):** A high-speed network technology primarily used for SANs. It offers very high throughput and low latency.
*   **iSCSI (Internet Small Computer System Interface):** A protocol that runs SCSI commands over standard Ethernet networks, allowing SANs to be built using existing LAN infrastructure. More cost-effective than Fibre Channel.

### ASCII Diagram: Simplified SAN Architecture

```
+-----------------------------------------------------------+
|                          SERVERS                          |
|  (Host Bus Adapters - HBAs)                               |
| +-----------+ +-----------+ +-----------+               |
| |  Server A | |  Server B | |  Server C |               |
| +-----------+ +-----------+ +-----------+               |
|       |           |           |                           |
|       -----------------------------------------------------
|                           SAN SWITCHES                     |
|                   (Dedicated High-Speed Network)           |
|       -----------------------------------------------------
|       |           |           |                           |
| +-----+-----+ +-----+-----+ +-----+-----+                 |
| | Storage Controller 1| | Storage Controller 2| | Storage Controller 3| |
| +-----------+ +-----------+ +-----------+               |
|       |           |           |                           |
|       -----------------------------------------------------
|                         DISK ARRAYS                        |
|                     (Block-level Storage)                  |
+-----------------------------------------------------------+
```

## 4.4 NAS (Network Attached Storage)

**Network Attached Storage (NAS)** is a file-level computer data storage server connected to a computer network that provides data access to a heterogeneous group of clients. NAS is specialized for serving files and is often deployed with commodity hardware and an embedded operating system.

### Key Characteristics of a NAS

1.  **File-Level Access:** Clients access storage as files and folders over a standard network protocol (like NFS for Unix/Linux or SMB/CIFS for Windows).
2.  **Integrated Device:** A NAS is typically a self-contained device with its own CPU, RAM, and storage disks, directly connected to the LAN.
3.  **Ease of Use:** Generally simpler to deploy and manage than a SAN, making it popular for small and medium-sized businesses (SMBs).
4.  **Cost-Effective:** Often more affordable than SAN solutions.
5.  **Scalability:** Scalable by adding more disk space or additional NAS units.

### ASCII Diagram: Simplified NAS Architecture

```
+---------------------------------------------------------------+
|                            CLIENTS                            |
|  (Desktops, Laptops, Servers on LAN)                          |
| +---------+ +---------+ +---------+                         |
| | Client A| | Client B| | Client C|                         |
| +---------+ +---------+ +---------+                         |
|       |         |         |                                   |
|       ---------------------------------------------------------
|                           LAN (Ethernet)                       |
|       ---------------------------------------------------------
|       |         |         |                                   |
|       +---------+---------+                                   |
|                 |                                             |
|                 +---------------------------------------------+
|                                                               |
|             +----------------------------------+              |
|             |          NAS Device              |              |
|             | +-----+    +----+    +-------+  |              |
|             | | CPU |----| RAM|----| Network|  |              |
|             | +-----+    +----+    +-------+  |              |
|             |       |                         |              |
|             |       +-------------------------+              |
|             |             DISK STORAGE                       |
|             |       (File-level Storage)                     |
|             +----------------------------------+              |
|                                                               |
+---------------------------------------------------------------+
```

### SAN vs. NAS Summary

| Feature        | SAN (Storage Area Network)                             | NAS (Network Attached Storage)                         |
|----------------|--------------------------------------------------------|--------------------------------------------------------|
| **Access Level** | Block-level                                            | File-level                                             |
| **Protocol**   | Fibre Channel, iSCSI                                   | NFS, SMB/CIFS                                          |
| **Network**    | Dedicated high-speed network (FC, iSCSI over Ethernet) | Standard Ethernet (LAN)                                |
| **Performance**| High throughput, low latency                           | Generally lower than SAN, depends on LAN congestion    |
| **Cost**       | Typically higher                                       | Generally lower                                        |
| **Use Case**   | Databases, virtualized servers (VMware, Hyper-V), high-performance apps | File shares, home directories, unstructured data, backups |
| **Complexity** | More complex to set up and manage                      | Simpler to deploy and manage                           |

## 4.5 RAID (Redundant Array of Independent Disks)

**RAID** is a data storage virtualization technology that combines multiple physical disk drives into a single logical unit for the purposes of data redundancy, performance improvement, or both. It's not virtualization in the same sense as VMs, but it abstracts physical disks into a logical volume, presenting a single, larger, or more resilient storage unit to the operating system.

### Common RAID Levels

1.  **RAID 0 (Striping):**
    *   **Purpose:** Performance. Data is split into blocks and written across multiple disks simultaneously ("striped").
    *   **Characteristics:** Highest performance (read/write), but **no fault tolerance**. If one disk fails, all data is lost.
    *   **Minimum Disks:** 2

2.  **RAID 1 (Mirroring):**
    *   **Purpose:** Redundancy. Data is written identically to two or more disks ("mirrored").
    *   **Characteristics:** Excellent read performance, good write performance, **high fault tolerance** (can lose all but one disk).
    *   **Minimum Disks:** 2
    *   **Drawback:** 50% storage efficiency (e.g., 2TB physical disks yield 1TB usable storage).

3.  **RAID 5 (Striping with Parity):**
    *   **Purpose:** Balance of performance and redundancy. Data is striped across disks, and parity information (for error recovery) is distributed across all disks.
    *   **Characteristics:** Good read performance, decent write performance, **can tolerate the failure of any one disk**.
    *   **Minimum Disks:** 3
    *   **Storage Efficiency:** (N-1)/N, where N is the number of disks (e.g., 3 disks = 66% efficiency).

4.  **RAID 10 (or RAID 1+0 - Striping of Mirrors):**
    *   **Purpose:** High performance and high redundancy. Data is striped across mirrored pairs of disks.
    *   **Characteristics:** Combines the speed of striping with the redundancy of mirroring. Very high performance and excellent fault tolerance (can lose one disk from each mirrored pair).
    *   **Minimum Disks:** 4 (in pairs of 2)
    *   **Storage Efficiency:** 50%.

> [!summary]
> SANs provide block-level storage access over a dedicated network for high-performance needs, while NAS offers file-level access over the LAN for ease of use. RAID combines multiple physical disks for redundancy, performance, or both, abstracting physical drives into a logical volume. All three are foundational to building robust storage for virtualized environments.

> [!tip]
> **Exam Focus:** Be able to differentiate SAN from NAS based on access level, protocols, and typical use cases. Understand the purpose and fault tolerance characteristics of common RAID levels (0, 1, 5, 10).

---
