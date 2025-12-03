---
title: "Unit IV, Topic 02: Introduction to Storage Virtualization"
id: unit4-topic2-storage-virt-intro
tags:
  - unit4
  - virtualization
  - storage-virtualization
  - block-storage
  - file-storage
  - address-remapping
alias:
  - Intro to Storage Virtualization
  - Block vs. File Virtualization
links:
  - "[[00_Syllabus]]"
  - "[[18_Unit_IV_Topic01_Memory_Virtualization]]"
  - "[[20_Unit_IV_Topic03_Risks_of_Storage_Virtualization]]"
---

# Unit IV, Topic 02: Introduction to Storage Virtualization

Just as server virtualization abstracts the server from its hardware, **Storage Virtualization** is the process of abstracting logical storage (what the user or server sees) from the physical storage (the actual disks and arrays).

It involves pooling physical storage resources from multiple network storage devices into what appears to be a single, centrally managed storage device. This virtual pool of storage can then be carved up and presented to servers or VMs as virtual disks.

## 4.2.1 Types of Storage Virtualization

Storage virtualization is primarily categorized by the level at which it operates: block or file.

### 1. Block-Level Storage Virtualization
-   **Concept:** This method abstracts storage at the level of data blocks. The virtualization layer intercepts I/O requests for data blocks and maps them to their physical location on any number of underlying storage devices. The host server or VM simply sees a logical disk (often called a Logical Unit Number or LUN) and is completely unaware of the underlying complexity or physical location of the data blocks.
-   **Characteristics:**
    -   High performance and low latency.
    -   The server's OS maintains its own file system on the raw blocks provided.
    -   This is the method used by **Storage Area Networks (SANs)**.
-   **Use Case:** Ideal for performance-sensitive applications that require raw disk access, such as databases (e.g., Oracle, SQL Server) and the operating system disks of virtual machines.

> [!quote] **Analogy: The Valet Parking Service**
> Block-level virtualization is like a valet service for your data. You (the server) hand over your car (a data block) to the valet (the virtualization layer). The valet parks it wherever there is space across multiple parking lots (physical disks/arrays) and gives you a simple ticket (the logical address). When you want your car back, you just give them the ticket; you don't need to know, nor do you care, which specific parking spot it's in.

### 2. File-Level Storage Virtualization
-   **Concept:** This method operates at a higher level, abstracting file systems. It can pool multiple file servers or **Network Attached Storage (NAS)** devices into a single, unified global namespace.
-   **Characteristics:**
    -   Users and applications access files through a single logical path (e.g., `\\global_share\documents\report.docx`), regardless of which physical server or NAS device the file is actually stored on.
    -   The virtualization layer manages the file systems.
    -   Simpler to implement and manage for unstructured data.
-   **Use Case:** Best for general-purpose file sharing, user home directories, and storing large amounts of unstructured data (documents, images, videos).

> [!quote] **Analogy: The Digital Library System**
> File-level virtualization is like a university's digital library system. You search for a book (a file) through a single web portal (the global namespace). The system finds and retrieves the book for you, regardless of which physical library building (NAS device) or shelf (physical server) it's located on.

## 4.2.2 Address Space Remapping

**Address space remapping** is the core engine that makes storage virtualization possible, particularly at the block level.

It is the process where the storage virtualization layer intercepts a write request from a server, which is targeted at a specific logical block address (LBA) on a virtual disk. The virtualization layer then translates, or **remaps**, that logical address to a different physical block address on one of the actual underlying storage devices.

This dynamic mapping is incredibly powerful and enables several advanced storage features:

-   **Thin Provisioning:** A virtual disk can be created with a large logical size (e.g., 1TB), but it only consumes physical storage space as data is actually written. The remapping function maps new writes to available physical space on the fly.
-   **Storage Tiering:** The remapping engine can automatically and non-disruptively move frequently accessed "hot" data blocks to a fast tier of storage (like SSDs) and infrequently accessed "cold" data blocks to a slower, cheaper tier (like HDDs), all without the server or VM being aware of the move.
-   **Non-Disruptive Migration:** Data can be moved from an old storage array to a new one with zero downtime, simply by updating the mapping in the virtualization layer to point the logical addresses to the new physical locations.

> [!success] **Exam Focus**
> -   **6-Mark Question:** "Differentiate between block-level and file-level storage virtualization."
>   -   **Answer Strategy:** Create a table or use bullet points.
>     -   **Abstraction Level:** Block-level abstracts raw data blocks; File-level abstracts file systems into a global namespace.
>     -   **Typical Technology:** Block-level is used in SANs; File-level is used in NAS.
>     -   **Use Case:** Block-level is for high-performance apps and databases; File-level is for general file sharing and unstructured data.
>     -   **Analogy:** Use the valet parking (block) vs. digital library (file) analogy to strengthen your explanation.
> -   **2-Mark Question:** "What is address space remapping?"
>   -   **Answer:** Address space remapping is the process in storage virtualization where the logical block address from a server's I/O request is translated to a different physical block address on an underlying storage device. This enables features like thin provisioning and storage tiering.
