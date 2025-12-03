---
title: "Unit IV, Topic 05: RAID"
id: unit4-topic5-raid
tags:
  - unit4
  - storage
  - raid
  - redundancy
  - performance
aliases:
  - Redundant Array of Independent Disks
  - RAID Levels
links:
  - "[[00_Syllabus]]"
  - "[[21_Unit_IV_Topic04_SAN_and_NAS]]"
  - "[[ClgMatx/SemVPrep/VirtX/Unit_04_Quiz]]"
---

# Unit IV, Topic 05: RAID

**RAID (Redundant Array of Independent Disks)** is a foundational storage virtualization technology that combines multiple physical disk drives into a single logical unit. The purpose of RAID is to provide **data redundancy** (protection against disk failure), **performance improvement**, or both.

A RAID controller (either hardware or software) presents a group of disks to the operating system as a single logical disk or volume. The OS is unaware of the underlying complexity.

## Common RAID Levels

There are many RAID levels, but the most common ones you will encounter and need to know for your exam are 0, 1, 5, and 10.

### RAID 0 (Striping)
-   **Purpose:** **Performance only.**
-   **How it works:** Data is split into blocks ("striped") and written across all disks in the array simultaneously. This parallel writing and reading dramatically increases performance.
-   **Characteristics:**
    -   Highest performance (both read and write).
    -   **No fault tolerance or redundancy.** If any single disk in the array fails, **all data is lost**.
    -   Storage Efficiency: 100% (e.g., two 1TB disks give you 2TB of usable space).
-   **Minimum Disks:** 2
-   **Use Case:** Temporary scratch space, video editing, or other situations where speed is paramount and data loss is not a concern (because data is backed up elsewhere).

### RAID 1 (Mirroring)
-   **Purpose:** **Redundancy only.**
-   **How it works:** Data is written identically to two or more disks, creating an exact copy or "mirror."
-   **Characteristics:**
    -   Excellent read performance (data can be read from any disk in the mirror).
    -   Write performance is equivalent to a single disk.
    -   **High fault tolerance.** The array can withstand the failure of all but one disk.
    -   Storage Efficiency: 50% (e.g., two 1TB disks give you only 1TB of usable space).
-   **Minimum Disks:** 2
-   **Use Case:** Operating system disks, small databases, or any situation where data protection is critical and capacity is a secondary concern.

### RAID 5 (Striping with Distributed Parity)
-   **Purpose:** **A balance of performance, capacity, and redundancy.**
-   **How it works:** Data is striped across multiple disks for performance. In addition, for each stripe of data, a "parity" block is calculated. This parity block, which can be used to reconstruct data in case of a disk failure, is written to a different disk in the array. The parity is distributed across all disks.
-   **Characteristics:**
    -   Good read performance.
    -   Decent write performance, but with a "write penalty" due to the need to calculate parity.
    -   **Can tolerate the failure of any one disk.**
    -   Storage Efficiency: (N-1)/N, where N is the number of disks (e.g., with 4 disks, you get 75% efficiency).
-   **Minimum Disks:** 3
-   **Use Case:** The workhorse of general-purpose storage. Good for file servers, application servers, and general virtualization workloads where a balance of cost, performance, and protection is needed.

### RAID 10 (or RAID 1+0 - A Stripe of Mirrors)
-   **Purpose:** **High performance AND high redundancy.**
-   **How it works:** This is a "nested" RAID level. It combines the mirroring of RAID 1 with the striping of RAID 0. First, disks are paired up into mirrors (RAID 1). Then, data is striped across these mirrored pairs (RAID 0).
-   **Characteristics:**
    -   Very high read and write performance (no parity calculation overhead).
    -   Excellent fault tolerance. Can tolerate the failure of at least one disk, and potentially more as long as no two disks from the same mirror fail.
    -   Storage Efficiency: 50% (same as RAID 1).
-   **Minimum Disks:** 4 (in pairs of 2).
-   **Use Case:** The gold standard for high-performance, mission-critical applications like large databases, email servers, and demanding virtualization workloads where both speed and data safety are paramount. It is more expensive than RAID 5 due to its lower capacity efficiency.

## Summary Table of RAID Levels

| RAID Level | Purpose                               | Min. Disks | Fault Tolerance      | Read Perf. | Write Perf. | Usable Capacity (N=disks, S=size) |
|------------|---------------------------------------|------------|----------------------|------------|-------------|-----------------------------------|
| **RAID 0** | Performance                           | 2          | **None**             | Excellent  | Excellent   | N * S                             |
| **RAID 1** | Redundancy                            | 2          | 1 disk failure (per pair) | Good       | Normal      | (N/2) * S                         |
| **RAID 5** | Balance (Perf, Capacity, Redundancy)  | 3          | 1 disk failure       | Good       | Fair        | (N-1) * S                         |
| **RAID 10**| High Perf & High Redundancy           | 4          | At least 1 disk failure | Excellent  | Excellent   | (N/2) * S                         |

> [!success] **Exam Focus**
> - **8-Mark Question:** "Explain the common RAID levels (0, 1, 5, and 10), detailing their purpose, fault tolerance, and a suitable use case for each."
>   - **Answer Strategy:** Go through each RAID level one by one. For each, state its name (e.g., RAID 0 - Striping), its primary purpose (Performance), its fault tolerance (None), and a typical use case (Video editing). Using the summary table as a guide for your answer is a highly effective strategy.
> - **Reasoning Question:** "A company needs to store its critical customer database. The top priorities are write performance and data protection. Which RAID level would you recommend and why?"
>   - **Answer:** Recommend **RAID 10**. Justify it by explaining that it offers the highest write performance (no parity overhead like RAID 5) and excellent data protection (mirroring), which are the two stated priorities. Acknowledge that while it is more expensive in terms of capacity than RAID 5, it is the appropriate choice for a mission-critical database where performance and safety cannot be compromised.
