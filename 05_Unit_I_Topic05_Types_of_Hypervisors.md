---
title: "Unit I, Topic 05: Types of Hypervisors"
id: unit1-topic5-hypervisor-types
tags:
  - unit1
  - virtualization
  - hypervisor
  - type-1-hypervisor
  - type-2-hypervisor
  - bare-metal
  - hosted
aliases:
  - Hypervisor Types
  - Bare-Metal vs. Hosted
links:
  - "[[04_Unit_I_Topic04_Types_of_Hardware_Virtualization]]"
  - "[[ClgMatx/SemVPrep/VirtX/Unit_01_Quiz]]"
---

# Unit I, Topic 05: Types of Hypervisors

A **hypervisor**, also known as a **Virtual Machine Monitor (VMM)**, is the core software that creates and runs virtual machines. It is the manager of the virtualized world. Based on its architecture and how it interacts with the physical hardware, we classify hypervisors into two main types.

## 5.1 Type-1 Hypervisor (Bare-Metal or Native)

A Type-1 hypervisor runs **directly on the host computer's hardware**, just like a traditional operating system would. There is no other software layer between it and the physical hardware. It *is* the operating system, a specialized one designed purely for running virtual machines.

### Architecture and Characteristics

-   **Direct Hardware Access:** Because it runs on "bare metal," it has direct and privileged access to all hardware resources, making it extremely efficient.
-   **High Performance:** Minimal overhead results in the best possible performance for guest VMs.
-   **High Security:** The attack surface is very small. There is no underlying general-purpose OS with potential vulnerabilities to compromise.
-   **Scalability & Robustness:** Designed for enterprise data centers and cloud infrastructure, capable of managing hundreds of VMs and providing advanced features.

#### ASCII Diagram: Type-1 Hypervisor

```ascii
+------------------------------------+
|  Guest OS 1  |  Guest OS 2  |  ... |
+------------------------------------+
|         TYPE-1 HYPERVISOR          |
+------------------------------------+
|          PHYSICAL HARDWARE         |
+------------------------------------+
```

> [!quote] **Analogy: The Purpose-Built Factory**
> A Type-1 hypervisor is like a factory built from the ground up for one purpose only: manufacturing cars (running VMs). The entire building, its layout, and its machinery are optimized for this single task, making it incredibly efficient and secure.

### Examples of Type-1 Hypervisors
-   **VMware ESXi:** The market leader in enterprise data centers.
-   **Microsoft Hyper-V:** A role within Windows Server or a standalone product (Hyper-V Server).
-   **KVM (Kernel-based Virtual Machine):** An open-source solution integrated into the Linux kernel, which allows the kernel itself to act as a Type-1 hypervisor.
-   **Citrix Hypervisor (formerly XenServer).**

## 5.2 Type-2 Hypervisor (Hosted)

A Type-2 hypervisor runs as a **software application on top of a conventional operating system** (the "host OS"). It relies on the host OS to manage hardware interactions.

### Architecture and Characteristics

-   **Runs as an App:** You install it just like any other program (e.g., like installing a web browser on Windows or macOS).
-   **Dependent on Host OS:** All hardware requests from the hypervisor are passed through the host OS, which introduces an extra layer of software and potential performance overhead.
-   **Lower Performance:** The competition for resources between the host OS and the hypervisor leads to lower performance compared to Type-1.
-   **Ease of Use:** Very simple to set up and use, making it ideal for individual users, developers, and testing.
-   **Lower Security:** A larger attack surface exists because both the host OS and the hypervisor can be potential targets. If the host OS crashes, all VMs crash with it.

#### ASCII Diagram: Type-2 Hypervisor

```ascii
+------------------------------------+
|  Guest OS 1  |  Guest OS 2  |  ... |
+------------------------------------+
|         TYPE-2 HYPERVISOR          |
|          (Application)             |
+------------------------------------+
|             HOST OS                |
|       (e.g., Windows, macOS)       |
+------------------------------------+
|          PHYSICAL HARDWARE         |
+------------------------------------+
```

> [!quote] **Analogy: The Workshop in a Garage**
> A Type-2 hypervisor is like setting up a small workshop (the hypervisor) inside your home garage (the Host OS). It's convenient and easy to get started, but you have to share space and power with the rest of the house, and the workshop's capabilities are limited by the garage's infrastructure.

### Examples of Type-2 Hypervisors
-   **Oracle VM VirtualBox:** Free, open-source, and very popular for desktop use.
-   **VMware Workstation** (for Windows/Linux) and **VMware Fusion** (for macOS).
-   **Parallels Desktop** (for macOS).

## Summary Table: Type-1 vs. Type-2 Hypervisors

| Feature          | Type-1 Hypervisor (Bare-Metal)                | Type-2 Hypervisor (Hosted)                   |
|------------------|-----------------------------------------------|----------------------------------------------|
| **Architecture** | Runs directly on hardware                     | Runs as an application on a host OS          |
| **Performance**  | **High** (direct hardware access)             | **Lower** (host OS overhead)                 |
| **Security**     | **High** (minimal attack surface)             | **Lower** (depends on host OS security)      |
| **Use Case**     | Enterprise data centers, cloud infrastructure | Personal use, development, testing           |
| **Examples**     | VMware ESXi, Hyper-V, KVM                     | VirtualBox, VMware Workstation, Parallels    |

> [!success] **Exam Focus**
> - **4-Mark Question:** "Differentiate between Type-1 and Type-2 hypervisors."
>   - **Answer Strategy:** This is a classic question. Use the summary table as your guide. Define each type based on its architecture (bare-metal vs. hosted). Compare them on performance, security, and primary use case. Providing examples for each is crucial for full marks.
> - **2-Mark Question:** "Give two examples of a Type-1 hypervisor."
>   - **Answer:** VMware ESXi and Microsoft Hyper-V.
> - **Reasoning Question:** "Why is a Type-1 hypervisor preferred for production enterprise environments?"
>   - **Answer:** A Type-1 hypervisor is preferred for production due to its superior **performance, security, and stability**. Because it runs directly on the hardware, it has minimal overhead and a smaller attack surface compared to a Type-2 hypervisor, which relies on a general-purpose host OS. These characteristics are essential for running business-critical applications.
