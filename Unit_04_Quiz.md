---
title: "Unit IV Quiz: Storage Virtualization"
id: unit4-quiz
tags: [quiz, unit4, storage-virtualization, memory-virtualization, san, nas, raid]
aliases: [Storage Virtualization Quiz]
links: ["[[00_Syllabus]]", "[[12_Unit_IV_Memory_Virtualization]]", "[[13_Unit_IV_Types_of_Storage_Virtualization]]", "[[14_Unit_IV_SAN_NAS_RAID]]"]
---

# Unit IV Quiz: Storage Virtualization

This quiz tests your understanding of Memory Virtualization, Storage Virtualization, SAN, NAS, and RAID concepts.

## 10 Quiz Questions (Multiple Choice / Short Answer)

1.  What is the process of mapping a Guest Physical Address (GPA) to a Host Physical Address (HPA) primarily handled by?
    a) The guest OS
    b) The hypervisor
    c) The application
    d) The network switch

2.  Which memory optimization technique involves the hypervisor injecting a driver into the guest OS to reclaim memory?
    a) Memory Overcommitment
    b) Transparent Page Sharing
    c) Memory Ballooning
    d) Memory Swapping

3.  What is the primary risk associated with Memory Overcommitment?
    a) Improved VM performance
    b) Severe performance degradation if all VMs demand full memory
    c) Increased hardware costs
    d) Reduced VM density

4.  Which storage virtualization type operates at the block level and is commonly used with SANs?
    a) File-level virtualization
    b) Block-level virtualization
    c) RAID 0
    d) NAS

5.  Which storage technology presents storage to clients as files and folders over a standard LAN using protocols like NFS or SMB?
    a) SAN
    b) NAS
    c) RAID 1
    d) Fibre Channel

6.  Which RAID level provides the highest performance but offers no fault tolerance?
    a) RAID 1
    b) RAID 5
    c) RAID 10
    d) RAID 0

7.  Which of the following is a key characteristic of a Storage Area Network (SAN)?
    a) File-level access
    b) Uses a shared LAN for traffic
    c) Block-level access over a dedicated network
    d) Simple to deploy for home use

8.  True or False: Transparent Page Sharing (TPS) saves memory by identifying and deduplicating identical memory pages across different VMs.

9.  Which RAID level provides mirroring for redundancy?
    a) RAID 0
    b) RAID 1
    c) RAID 5
    d) RAID 6

10. What is "address space remapping" in storage virtualization used for?
    a) To permanently assign virtual addresses to physical blocks
    b) To dynamically translate virtual block addresses to physical block addresses
    c) To manage IP address allocation
    d) To format physical disks

## 10 Reasoning Questions

1.  Explain the two-level memory translation process in a virtualized environment. Why is this necessary?
2.  Compare and contrast Memory Ballooning and Host-level Memory Swapping. Which one is preferable, and why?
3.  Discuss the primary differences between block-level and file-level storage virtualization, providing a clear use case for each.
4.  Why is a SAN typically preferred over a NAS for high-performance applications like large databases?
5.  Explain how RAID 5 works and describe its balance between performance, storage efficiency, and redundancy.
6.  A company is experiencing performance issues with its virtualized environment. Upon investigation, they find that the hypervisor is frequently swapping VM memory to disk. What memory optimization technique is likely misconfigured or overused, and what is the consequence?
7.  Describe the concept of "storage tiering" and how address space remapping enables it.
8.  What is the "Single Point of Failure" risk in storage virtualization, and how can it be mitigated?
9.  You need to set up a storage array for a video editing workstation that requires both high performance and protection against a single disk failure. Which RAID level (0, 1, 5, 10) would be the most suitable choice, and why?
10. If you have four 2TB disks, what would be the total usable capacity for RAID 1, RAID 5, and RAID 10 configurations?

## 10 Real-World Cases

1.  **Case:** A company runs many virtual desktops, all using the same Windows 10 "golden image." They are looking to maximize the number of VMs they can run on their physical hosts.
    *   **Question:** Which memory optimization technique would be most effective in this scenario, and why?

2.  **Case:** An IT department needs to provide centralized, high-performance storage for its cluster of VMware ESXi hosts to enable features like vMotion (live migration).
    *   **Question:** Which storage networking technology (SAN or NAS) is traditionally required for this, and what access level does it provide?

3.  **Case:** A small marketing department needs a simple, cost-effective solution for sharing large media files (videos, images, documents) among its team members' Windows and Mac computers.
    *   **Question:** Which storage solution would be the most appropriate and easiest to deploy?

4.  **Case:** A database administrator is designing a storage solution for a new critical database. The primary requirements are the highest possible write performance and excellent redundancy.
    *   **Question:** Which RAID level would best meet these requirements?

5.  **Case:** A virtual host is running low on physical RAM. One of its VMs is idle but has a large amount of memory allocated to it. The hypervisor needs to reclaim this memory for another, busier VM.
    *   **Question:** What memory management technique would the hypervisor use to "ask" the idle VM to release its unused memory?

6.  **Case:** A financial services company needs to store transaction logs. They need a storage solution that offers redundancy but are on a tight budget and want to maximize storage capacity. They can tolerate slightly slower write performance.
    *   **Question:** Which RAID level offers a good compromise between redundancy and storage efficiency for this use case?

7.  **Case:** An administrator notices that I/O performance on their virtualized storage is suffering because all the high-demand VMs are accessing data from the same physical disk array.
    *   **Question:** What feature enabled by address space remapping could help alleviate this issue?

8.  **Case:** A law firm wants to implement storage virtualization but is highly concerned about the risk of losing access to all their data if a single component fails.
    *   **Question:** What is this risk called, and what is the primary mitigation strategy they should implement for their storage controllers?

9.  **Case:** A company uses iSCSI to connect its servers to a storage array.
    *   **Question:** What type of storage network are they using, and what is the benefit of using iSCSI?

10. **Case:** A user needs a simple way to store large backups. Performance is not a major concern, but they want the fastest possible rebuild time in case of a single disk failure and don't want to deal with complex parity calculations.
    *   **Question:** Between RAID 1 and RAID 5, which would be simpler and faster to rebuild, and why?

## 10 Rapid Fire Questions

1.  What does RAID stand for?
2.  True or False: A SAN provides file-level access.
3.  Name one protocol used by NAS.
4.  Which RAID level offers no redundancy?
5.  What hardware feature in modern CPUs assists with memory virtualization?
6.  What does SAN stand for?
7.  In RAID 1, if you have two 4TB disks, what is the usable capacity?
8.  Which is generally more expensive and complex: SAN or NAS?
9.  What is "memory ballooning"?
10. Is host-level swapping desirable for VM performance? (Yes/No)

## All Possible 2-Mark Remember Questions

1.  Define Memory Virtualization.
2.  What is the two-level memory translation process?
3.  Explain Memory Overcommitment.
4.  What is Transparent Page Sharing (TPS)?
5.  Define Storage Virtualization.
6.  Differentiate between block-level and file-level storage virtualization.
7.  What is a SAN?
8.  What is a NAS?
9.  Define RAID.
10. What is RAID 0 (Striping)?
11. What is RAID 1 (Mirroring)?
12. What is RAID 5 (Striping with Parity)?
13. What is RAID 10 (Striping of Mirrors)?
14. List two risks of storage virtualization.
15. What is address space remapping?

## Problems

No specific problems for Unit IV that require mathematical calculation or step-by-step setup, as it's primarily a conceptual unit. The Reasoning and Real-World Cases sections cover problem-solving scenarios.

## Answers

### 10 Quiz Questions - Answers
1.  **1. b) The hypervisor** - **Concept:** The hypervisor manages the mapping between the guest's perceived physical memory and the host's actual physical memory.
2.  **2. c) Memory Ballooning** - **Concept:** A balloon driver in the guest OS inflates to force the guest to reclaim its own memory, which the hypervisor can then use elsewhere.
3.  **3. b) Severe performance degradation if all VMs demand full memory** - **Concept:** Overcommitment relies on VMs not using their full allocation. If they do, the host must swap to slow disk storage.
4.  **4. b) Block-level virtualization** - **Concept:** This method virtualizes storage at the block level, which is how SANs operate.
5.  **5. b) NAS** - **Concept:** Network Attached Storage provides file-level access over standard network protocols like SMB or NFS.
6.  **6. d) RAID 0** - **Concept:** RAID 0 (Striping) splits data across disks for performance but has no redundancy. If one disk fails, all data is lost.
7.  **7. c) Block-level access over a dedicated network** - **Concept:** SANs are dedicated networks providing block-level storage.
8.  **8. True** - **Concept:** TPS deduplicates identical memory pages across multiple VMs to save physical RAM.
9.  **9. b) RAID 1** - **Concept:** RAID 1 (Mirroring) writes identical data to two or more disks for redundancy.
10. **10. b) To dynamically translate virtual block addresses to physical block addresses** - **Concept:** This is the core function of address remapping, enabling features like tiering and migration.

### 10 Reasoning Questions - Answers
1.  **1. Explanation:** In a virtualized environment, there are two layers of address translation. First, the guest OS translates Guest Virtual Addresses (GVAs) from applications into Guest Physical Addresses (GPAs). The guest OS believes GPAs are actual RAM. Second, the hypervisor (with hardware assistance) translates these GPAs into Host Physical Addresses (HPAs), which are the actual locations in the host's physical RAM. This is necessary because the hypervisor needs to manage memory for multiple VMs, and cannot give any single VM direct, exclusive control over the physical hardware.
2.  **2. Comparison:**
    *   **Memory Ballooning:** A cooperative technique where the hypervisor asks the guest OS to free up memory by using a balloon driver. The guest OS decides which (less important) pages to page out to its own virtual disk.
    *   **Host-level Swapping:** A non-cooperative, last-resort technique where the hypervisor forcibly takes memory pages from a VM and writes them to a swap file on the host's disk.
    *   **Preference:** Memory Ballooning is highly preferable because the guest OS, which has insight into its own memory usage, can make intelligent decisions about what to page out, minimizing the performance impact. Host-level swapping is indiscriminate and leads to severe performance degradation.
3.  **3. Differences:**
    *   **Block-Level:** Virtualizes storage at the level of data blocks (raw storage volumes). It's ignorant of the file system. **Use Case:** High-performance databases, VM operating system disks, or applications requiring raw disk access, typically in a SAN environment.
    *   **File-Level:** Virtualizes storage at the file system level, creating a unified global namespace. It manages files and folders. **Use Case:** General-purpose file sharing for end-users, storing unstructured data like documents and media files, typically in a NAS environment.
4.  **4. Explanation:** A SAN is preferred for high-performance applications like large databases for two main reasons:
    *   **Block-Level Access:** Databases are optimized to perform I/O operations at the block level, and a SAN provides this direct, low-level access.
    *   **Dedicated Network:** A SAN uses a dedicated, high-speed network (like Fibre Channel or dedicated iSCSI Ethernet) for storage traffic, which avoids contention with general LAN traffic and ensures low latency and high throughput. A NAS, in contrast, shares the general LAN, which can lead to performance bottlenecks.
5.  **5. Explanation:** RAID 5 uses "striping with distributed parity." Data is striped across multiple disks for performance, similar to RAID 0. However, for each stripe, a "parity" block is calculated and written to one of the disks in the array. This parity information is distributed across all disks in the array. If any single disk fails, the data on that failed disk can be reconstructed using the data and parity information from the remaining disks.
    *   **Balance:** It offers good read performance, decent write performance (though with a penalty due to parity calculation), good storage efficiency (N-1 usable disks), and can tolerate the failure of one disk.
6.  **6. Problem:** The company is likely suffering from excessive **Memory Overcommitment**. This means more virtual memory has been allocated to VMs than physically available. When the VMs demand this memory, the hypervisor runs out of physical RAM and is forced to use **host-level swapping**. The consequence is **severe performance degradation** for the affected VMs because accessing data from a disk (swap file) is orders of magnitude slower than accessing it from RAM.
7.  **7. Explanation:** **Storage tiering** is a policy-based technique where data is automatically moved between different tiers of storage based on its access frequency. For example, frequently accessed "hot" data is placed on high-performance, expensive storage (like SSDs), while infrequently accessed "cold" data is moved to lower-cost, high-capacity storage (like HDDs). **Address space remapping** enables this by allowing the storage virtualization layer to change the physical location of a data block without changing its logical address, making the data movement completely transparent to the host server or VM.
8.  **8. Risk and Mitigation:**
    *   **Risk:** The "Single Point of Failure" (SPOF) risk in storage virtualization is that the virtualization layer itself (e.g., the storage controller or appliance) could fail, causing a complete loss of access to all the storage it manages.
    *   **Mitigation:** The primary mitigation strategy is **redundancy**. This is typically achieved by implementing dual or clustered storage controllers in an active-active or active-passive configuration, so if one controller fails, the other can take over seamlessly.
9.  **9. Answer:** **RAID 10 (or RAID 1+0)** would be the most suitable choice.
    *   **Why:** It offers both high performance and high redundancy. It provides the excellent read/write performance of striping (RAID 0) and the excellent data protection of mirroring (RAID 1). While RAID 5 offers single-disk redundancy, its write performance suffers from a "parity penalty," which can be a bottleneck for video editing. RAID 10 has a faster write performance than RAID 5 and can often tolerate multiple disk failures (as long as no two disks from the same mirror fail).
10. **10. Usable Capacity:**
    *   **RAID 1 (Mirroring):** With four 2TB disks, you would mirror them in pairs, resulting in **4TB** of usable storage. (Or, if mirroring all four, only 2TB, but typically it's pairs).
    *   **RAID 5 (Striping with Parity):** Usable capacity is (N-1) * disk size, where N is the number of disks. So, (4-1) * 2TB = **6TB** of usable storage.
    *   **RAID 10 (Striping of Mirrors):** This uses N/2 capacity. So, with four 2TB disks, you get **4TB** of usable storage.

### 10 Rapid Fire Questions - Answers
1.  **1. What does RAID stand for?** Redundant Array of Independent Disks
2.  **2. True or False: A SAN provides file-level access.** False
3.  **3. Name one protocol used by NAS.** NFS (Network File System) OR SMB/CIFS (Server Message Block / Common Internet File System)
4.  **4. Which RAID level offers no redundancy?** RAID 0
5.  **5. What hardware feature in modern CPUs assists with memory virtualization?** Intel EPT (Extended Page Tables) OR AMD RVI (Rapid Virtualization Indexing) / NPT (Nested Page Tables)
6.  **6. What does SAN stand for?** Storage Area Network
7.  **7. In RAID 1, if you have two 4TB disks, what is the usable capacity?** 4TB
8.  **8. Which is generally more expensive and complex: SAN or NAS?** SAN
9.  **9. What is "memory ballooning"?** A technique where a driver in the guest OS reclaims memory for the hypervisor.
10. **10. Is host-level swapping desirable for VM performance? (Yes/No)** No

### All Possible 2-Mark Remember Questions - Answers
1.  **1. Define Memory Virtualization.** Memory virtualization is the technique of abstracting physical RAM from virtual machines, allowing a hypervisor to manage and allocate memory efficiently and securely.
2.  **2. What is the two-level memory translation process?** It involves two steps: first, the guest OS translates a Guest Virtual Address (GVA) to a Guest Physical Address (GPA); second, the hypervisor translates the GPA to a Host Physical Address (HPA).
3.  **3. Explain Memory Overcommitment.** Memory overcommitment is the practice of allocating more total virtual memory to VMs than the physical memory available on the host, relying on the fact that not all VMs will use their full allocation simultaneously.
4.  **4. What is Transparent Page Sharing (TPS)?** TPS is a memory optimization technique where the hypervisor deduplicates identical memory pages across multiple VMs, storing only one physical copy to save memory.
5.  **5. Define Storage Virtualization.** Storage virtualization is the process of pooling physical storage from multiple devices into a single, centrally managed storage pool, abstracting the logical storage from its physical location.
6.  **6. Differentiate between block-level and file-level storage virtualization.** Block-level virtualization presents raw storage volumes (blocks) to servers, typically over a SAN, for high performance. File-level virtualization presents a unified file system namespace, typically over a NAS, for easy file sharing.
7.  **7. What is a SAN?** A SAN (Storage Area Network) is a dedicated, high-speed network that provides block-level storage access from centralized storage arrays to servers.
8.  **8. What is a NAS?** A NAS (Network Attached Storage) is a self-contained device connected to a LAN that provides file-level storage access to clients over standard network protocols.
9.  **9. Define RAID.** RAID (Redundant Array of Independent Disks) is a technology that combines multiple physical disks into a single logical unit for data redundancy, performance improvement, or both.
10. **10. What is RAID 0 (Striping)?** RAID 0 is a RAID level that stripes data across multiple disks for increased performance but provides no fault tolerance.
11. **11. What is RAID 1 (Mirroring)?** RAID 1 is a RAID level that mirrors data across two or more disks, providing high redundancy but with 50% storage efficiency.
12. **12. What is RAID 5 (Striping with Parity)?** RAID 5 is a RAID level that stripes data and distributed parity information across three or more disks, providing a balance of performance, efficiency, and tolerance for a single disk failure.
13. **13. What is RAID 10 (Striping of Mirrors)?** RAID 10 is a RAID level that combines striping and mirroring (RAID 1+0), offering both high performance and high redundancy.
14. **14. List two risks of storage virtualization.** Single Point of Failure (SPOF), Increased Complexity. (Performance Bottlenecks, Vendor Lock-in, Data Loss Potential also acceptable).
15. **15. What is address space remapping?** It is the process in storage virtualization where the virtualization layer translates a logical or virtual block address from a server to a different physical block address on a storage device.
