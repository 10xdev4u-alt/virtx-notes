---
title: "Unit IV Quiz: Memory and Storage Virtualization"
id: unit4-quiz
tags:
  - quiz
  - unit4
  - storage-virtualization
  - memory-virtualization
  - san
  - nas
  - raid
aliases:
  - Storage and Memory Virtualization Quiz
links:
  - "[[ClgMatx/SemVPrep/CNx/00_Syllabus]]"
  - "[[18_Unit_IV_Topic01_Memory_Virtualization]]"
  - "[[19_Unit_IV_Topic02_Storage_Virtualization_Intro]]"
  - "[[20_Unit_IV_Topic03_Risks_of_Storage_Virtualization]]"
  - "[[21_Unit_IV_Topic04_SAN_and_NAS]]"
  - "[[22_Unit_IV_Topic05_RAID]]"
---

# Unit IV Quiz: Memory and Storage Virtualization

This quiz tests your understanding of Memory Virtualization, Storage Virtualization, SAN, NAS, and RAID concepts.

## 1. 10 Quiz Questions (Multiple Choice / Short Answer)

1.  What is the process of mapping a Guest Physical Address (GPA) to a Host Physical Address (HPA) primarily handled by?
    a) The guest OS
    b) The hypervisor
    c) The application
    d) The network switch

2.  Which memory optimization technique involves the hypervisor injecting a driver into the guest OS to cooperatively reclaim memory?
    a) Memory Overcommitment
    b) Transparent Page Sharing
    c) Memory Ballooning
    d) Host-level Swapping

3.  What is the primary risk associated with Memory Overcommitment?
    a) Improved VM performance
    b) Severe performance degradation if all VMs demand their full memory
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

## 2. 10 Reasoning Questions

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

## 3. 10 Real-World Cases

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

## 4. 10 Rapid Fire Questions

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

## 5. All Possible 2-Mark Remember Questions

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

---
---

## Answers

### 1. 10 Quiz Questions - Answers
1.  **Answer:** b) The hypervisor
    - **Concept:** The hypervisor manages the mapping between the guest's perceived physical memory (GPA) and the host's actual physical memory (HPA).
2.  **Answer:** c) Memory Ballooning
    - **Concept:** A balloon driver within the guest OS inflates to force the guest to reclaim its own memory, which the hypervisor can then use for other VMs.
3.  **Answer:** b) Severe performance degradation if all VMs demand their full memory
    - **Concept:** Overcommitment relies on VMs not using their full allocation. If they do, the host must swap to slow disk storage, causing a performance collapse.
4.  **Answer:** b) Block-level virtualization
    - **Concept:** This method virtualizes storage at the raw data block level, which is the native access method for SANs.
5.  **Answer:** b) NAS
    - **Concept:** Network Attached Storage is a file server that provides access via file-based protocols like NFS (for Linux/Unix) and SMB (for Windows).
6.  **Answer:** d) RAID 0
    - **Concept:** RAID 0 (Striping) splits data across all disks for maximum performance but provides no redundancy. If one disk fails, all data is lost.
7.  **Answer:** c) Block-level access over a dedicated network
    - **Concept:** SANs are dedicated networks (Fibre Channel or iSCSI) that provide block-level storage access to servers.
8.  **Answer:** True
    - **Concept:** TPS is a memory deduplication technique where the hypervisor finds identical memory pages across VMs and stores only one physical copy.
9.  **Answer:** b) RAID 1
    - **Concept:** RAID 1 (Mirroring) writes identical data to two or more disks, providing high redundancy.
10. **Answer:** b) To dynamically translate virtual block addresses to physical block addresses
    - **Concept:** This is the core function of address remapping, which enables advanced features like thin provisioning, tiering, and non-disruptive migration.

### 2. 10 Reasoning Questions - Answers
1.  **Explanation:** In a virtualized environment, there are two levels of translation. First, the guest OS translates an application's Guest Virtual Address (GVA) into a Guest Physical Address (GPA). Second, the hypervisor translates that GPA into a Host Physical Address (HPA) in actual RAM. This is necessary to allow the hypervisor to manage a shared pool of memory for multiple VMs, ensuring they remain isolated and do not conflict with each other's memory space.
2.  **Comparison:**
    *   **Memory Ballooning:** A cooperative technique where the hypervisor uses a driver to ask the guest OS to give up its least important memory pages.
    *   **Host-level Swapping:** A last-resort, non-cooperative technique where the hypervisor forcibly takes memory pages from a VM and writes them to slow disk storage.
    *   **Preference:** Memory Ballooning is highly preferable. The guest OS knows which memory pages are important, so it can make an intelligent decision, minimizing the performance impact. Host-level swapping is indiscriminate and severely degrades VM performance.
3.  **Differences:**
    *   **Block-Level:** Abstracts raw data blocks. The server OS formats the storage with a file system. **Use Case:** High-performance databases or VM OS disks on a SAN.
    *   **File-Level:** Abstracts file systems into a global namespace. The storage device manages the file system. **Use Case:** General-purpose file sharing for users or storing unstructured data on a NAS.
4.  **Explanation:** A SAN is preferred for large databases because it provides **block-level access**, which is what databases are optimized for, and it uses a **dedicated, high-speed network** (like Fibre Channel or iSCSI), which guarantees low latency and high throughput without contention from regular user traffic. A NAS uses the shared LAN and provides file-level access, both of which introduce overhead that can be a bottleneck for demanding database applications.
5.  **Explanation:** RAID 5 uses "striping with distributed parity." Data is striped across all disks for performance. A parity block is calculated for each stripe and written to a different disk in the array. This provides a balance: good read performance, good storage efficiency (N-1 usable disks), and the ability to tolerate the failure of any single disk.
6.  **Problem:** The company is suffering from excessive **Memory Overcommitment**. When the VMs' active memory demand exceeds the available physical RAM, the hypervisor is forced to use **host-level swapping**. The consequence is **severe performance degradation** for the VMs, as accessing data from a disk (swap file) is thousands of times slower than from RAM.
7.  **Explanation:** **Storage tiering** is a technique where data is automatically moved between different tiers of storage based on access frequency. "Hot" (frequently accessed) data is kept on fast, expensive storage (SSDs), while "cold" (infrequently accessed) data is moved to slow, cheap storage (HDDs). **Address space remapping** enables this by allowing the virtualization layer to change the physical location of a data block without the server being aware, making the movement between tiers transparent.
8.  **Risk and Mitigation:**
    *   **Risk:** The "Single Point of Failure" (SPOF) risk is that the central storage virtualization controller itself could fail, causing a complete loss of access to all storage.
    *   **Mitigation:** The primary mitigation is **redundancy**, typically by implementing dual or clustered storage controllers in an active-active or active-passive configuration, so one can take over if the other fails.
9.  **Answer:** **RAID 10 (RAID 1+0)** would be the most suitable choice.
    *   **Why:** It provides the best combination of performance and redundancy for this use case. It offers the high write performance of striping (RAID 0) without the parity calculation overhead of RAID 5, which is crucial for video editing. It also provides excellent redundancy through mirroring (RAID 1), protecting against a single disk failure.
10. **Usable Capacity:** (4 disks * 2TB each = 8TB total physical capacity)
    *   **RAID 1 (as two mirrored pairs):** 4TB usable capacity.
    *   **RAID 5:** (4-1) * 2TB = 6TB usable capacity.
    *   **RAID 10:** (4/2) * 2TB = 4TB usable capacity.

### 3. 10 Real-World Cases - Answers
1.  **Solution:** **Transparent Page Sharing (TPS)** would be most effective. Since all VMs use the same "golden image," their memory will contain many identical pages (for OS files, common libraries, etc.). TPS would deduplicate these pages, storing only one physical copy and freeing up a significant amount of RAM, allowing more VMs to run on the hosts.
2.  **Solution:** A **Storage Area Network (SAN)** is traditionally required. It provides the **block-level** shared storage that hypervisor cluster file systems (like VMware's VMFS) need to allow all hosts in the cluster to see and access the same VM files simultaneously, which is a prerequisite for features like vMotion.
3.  **Solution:** A **Network Attached Storage (NAS)** device would be the most appropriate and easiest solution. It's cost-effective, simple to deploy on their existing LAN, and provides straightforward file-level sharing accessible by both Windows (via SMB) and Mac (via SMB or NFS) computers.
4.  **Solution:** **RAID 10 (RAID 1+0)** would best meet these requirements. It offers the highest write performance (no parity overhead) and excellent redundancy, making it the standard choice for mission-critical databases.
5.  **Solution:** The hypervisor would use **Memory Ballooning**. It would instruct the balloon driver in the idle VM to "inflate," causing the idle guest OS to release its unused memory pages, which the hypervisor can then reclaim and allocate to the busier VM.
6.  **Solution:** **RAID 5** offers the best compromise. It provides protection against a single disk failure while offering much better storage efficiency ((N-1)/N) than RAID 1 or RAID 10, which is important for a budget-conscious scenario. The write performance penalty is an acceptable trade-off.
7.  **Solution:** **Storage Tiering** and **Load Balancing**, both enabled by address space remapping, could alleviate this. Storage tiering could move the hot blocks to faster disks, while load balancing could redistribute the I/O requests across multiple physical arrays to prevent a single one from being overwhelmed.
8.  **Solution:** This risk is called a **Single Point of Failure (SPOF)**. The primary mitigation strategy is to implement **redundant storage controllers** in a high-availability (HA) pair, so if one controller fails, the other takes over seamlessly.
9.  **Solution:** They are using a **Storage Area Network (SAN)**. The benefit of using iSCSI is that it allows them to build their SAN using standard, cost-effective Ethernet networking hardware instead of expensive and specialized Fibre Channel equipment.
10. **Solution:** **RAID 1** would be simpler and faster to rebuild. In case of a failure, the data is simply copied from the surviving mirror disk. In RAID 5, the data on the failed disk must be reconstructed by reading from all other surviving disks and performing parity calculations, which is a much more intensive and time-consuming process.

### 4. 10 Rapid Fire Questions - Answers
1.  **What does RAID stand for?** Redundant Array of Independent Disks.
2.  **True or False: A SAN provides file-level access.** False.
3.  **Name one protocol used by NAS.** NFS or SMB/CIFS.
4.  **Which RAID level offers no redundancy?** RAID 0.
5.  **What hardware feature in modern CPUs assists with memory virtualization?** Intel EPT or AMD RVI/NPT.
6.  **What does SAN stand for?** Storage Area Network.
7.  **In RAID 1, if you have two 4TB disks, what is the usable capacity?** 4TB.
8.  **Which is generally more expensive and complex: SAN or NAS?** SAN.
9.  **What is "memory ballooning"?** A technique where a guest driver reclaims memory for the hypervisor.
10. **Is host-level swapping desirable for VM performance? (Yes/No)** No.

### 5. All Possible 2-Mark Remember Questions - Answers
1.  **Define Memory Virtualization.** It is the technique of abstracting a VM's memory from the host's physical RAM, managed by the hypervisor through a two-level address translation process.
2.  **What is the two-level memory translation process?** It involves the guest OS translating a GVA to a GPA, and then the hypervisor translating the GPA to an HPA in physical RAM.
3.  **Explain Memory Overcommitment.** It is the practice of allocating more total virtual RAM to VMs than the physical RAM available on the host.
4.  **What is Transparent Page Sharing (TPS)?** It is a memory deduplication technique where a hypervisor stores only one physical copy of identical memory pages shared by multiple VMs.
5.  **Define Storage Virtualization.** It is the process of pooling physical storage from multiple devices into a single, centrally managed storage pool, abstracting logical storage from its physical location.
6.  **Differentiate between block-level and file-level storage virtualization.** Block-level (used in SANs) presents raw storage volumes, while file-level (used in NAS) presents a unified file system.
7.  **What is a SAN?** A SAN is a dedicated, high-speed network that provides servers with block-level access to consolidated storage.
8.  **What is a NAS?** A NAS is a self-contained storage device connected to a LAN that provides file-level access to clients.
9.  **Define RAID.** RAID is a technology that combines multiple physical disks into a single logical unit for data redundancy, performance, or both.
10. **What is RAID 0 (Striping)?** RAID 0 is a RAID level that stripes data across multiple disks for increased performance but provides no fault tolerance.
11. **What is RAID 1 (Mirroring)?** RAID 1 is a RAID level that mirrors data across two or more disks, providing high redundancy at the cost of 50% capacity efficiency.
12. **What is RAID 5 (Striping with Parity)?** RAID 5 is a RAID level that stripes data and distributed parity across three or more disks, providing a balance of performance, capacity, and single-disk fault tolerance.
13. **What is RAID 10 (Striping of Mirrors)?** RAID 10 is a nested RAID level that stripes data across mirrored pairs of disks, offering both high performance and high redundancy.
14. **List two risks of storage virtualization.** 1) Single Point of Failure (SPOF). 2) Increased management complexity.
15. **What is address space remapping?** It is the process where a storage virtualization layer translates a logical block address from a server to a different physical block address on a storage device, enabling features like tiering.
