---
title: "Unit IV: Memory Virtualization"
id: unit4-memory-virtualization
tags: [virtualization, memory-virtualization, unit4, paging, swapping, ballooning, tlb]
aliases: [Virtual Memory, Memory Management]
links: ["[[00_Syllabus]]", "[[11_Unit_III_VLAN_and_WAN_Virtualization]]"]
---

# Unit IV: Memory Virtualization

Welcome to Unit IV! After exploring compute and network resources, we now turn our attention to **Memory Virtualization**, a crucial aspect that ensures efficient and secure memory management in virtualized environments.

## 4.1 Memory Virtualization

**Memory Virtualization** is the technique that allows a guest operating system within a Virtual Machine (VM) to use a virtual memory address space, which is then mapped by the hypervisor to the host's physical memory. This gives each VM the impression that it has access to its own dedicated, contiguous block of memory, even though the hypervisor might be dynamically allocating and remapping physical memory across multiple VMs.

### Key Concepts in Memory Virtualization

1.  **Virtual Memory (OS concept):**
    *   This is a fundamental concept in modern operating systems, even without virtualization. The OS provides each process with a large, private virtual address space. The CPU's Memory Management Unit (MMU) translates these virtual addresses to physical addresses in RAM. If RAM runs out, parts of memory are "paged" or "swapped" to disk.
    *   **Goal:** To provide processes with more memory than physically available and to isolate processes from each other.

2.  **Two Levels of Translation in Virtualization:**
    *   In a virtualized environment, there are two layers of virtual-to-physical address translation:
        1.  **Guest Virtual Address (GVA) to Guest Physical Address (GPA):** This is the translation performed by the guest OS's MMU for its processes. The guest OS believes GPA is actual physical memory.
        2.  **Guest Physical Address (GPA) to Host Physical Address (HPA):** This is the translation performed by the hypervisor (or hardware) to map the guest's "physical" memory requests to the *actual* physical memory on the host.

    **ASCII Diagram: Two-Level Memory Translation**

    ```
    +-------------------------------------------------+
    |              Guest OS / Applications            |
    |                                                 |
    |  Application Process (Virtual Address Space)    |
    |  +-------------------------------------------+  |
    |  |  Guest Virtual Address (GVA)              |  |
    |  +-------------------------------------------+  |
    |      v (Guest OS Paging/MMU)                   |
    |  +-------------------------------------------+  |
    |  |  Guest Physical Address (GPA)             |  |
    |  +-------------------------------------------+  |
    +-------------------------------------------------+
    |                   HYPERVISOR                    |
    |      v (Hypervisor / Hardware MMU)              |
    |  +-------------------------------------------+  |
    |  |  Host Physical Address (HPA)              |  |
    |  +-------------------------------------------+  |
    +-------------------------------------------------+
    |               PHYSICAL RAM (Host)               |
    +-------------------------------------------------+
    ```

### Memory Optimization Techniques (Used by Hypervisors)

Hypervisors employ various techniques to manage and optimize memory usage across multiple VMs:

1.  **Memory Ballooning:**
    *   **Concept:** The hypervisor injects a "balloon driver" into the guest OS. This driver artificially inflates its memory usage, causing the guest OS to perform its own memory reclamation (paging out less used pages to disk *within the VM*). This effectively "frees up" physical memory on the host that the hypervisor can then allocate to other VMs that need it more.
    *   **Benefit:** Allows the hypervisor to reclaim unused memory from less busy VMs without causing host-level swapping.

2.  **Memory Overcommitment (or Oversubscription):**
    *   **Concept:** The hypervisor allocates more virtual memory to all VMs combined than the physical memory actually available on the host. It relies on the assumption that not all VMs will use all their allocated memory at the same time.
    *   **Benefit:** Increases VM density (more VMs per physical host).
    *   **Risk:** If all VMs simultaneously demand their full allocated memory, the host will have to swap to disk (host-level swapping), leading to severe performance degradation.

3.  **Transparent Page Sharing (TPS):**
    *   **Concept:** The hypervisor scans the memory pages of different VMs to identify identical content. If it finds identical pages (e.g., from multiple VMs running the same OS or application code), it stores only one physical copy of that page and maps all VMs requiring that content to this single physical page.
    *   **Benefit:** Significant memory savings, especially when running many similar VMs.

4.  **Memory Swapping (Host-level):**
    *   **Concept:** If the hypervisor runs out of physical RAM and cannot reclaim memory through ballooning or TPS, it will swap entire VM memory pages to a designated swap file on the host's disk.
    *   **Risk:** This is a last resort and severely impacts VM performance due to slow disk I/O.

### Hardware Support for Memory Virtualization

Modern CPUs often include hardware features to assist memory virtualization, such as Intel's **Extended Page Tables (EPT)** and AMD's **Rapid Virtualization Indexing (RVI)** (also known as Nested Page Tables - NPT). These technologies streamline the GPA to HPA translation, offloading some of the hypervisor's work to the hardware and significantly reducing memory virtualization overhead.

> [!summary]
> Memory virtualization provides isolated virtual memory spaces to VMs, managed by the hypervisor through a two-level translation process. Techniques like ballooning, overcommitment, and transparent page sharing optimize memory usage, while hardware support (EPT/RVI) enhances performance.

> [!tip]
> **Exam Focus:** Understand the two-level translation process. Be able to explain memory ballooning, overcommitment, and transparent page sharing, including their benefits and potential risks (especially overcommitment leading to host-level swapping). Know the role of hardware assists like EPT/RVI.

---
