---
title: "Unit I: Types of Hypervisors"
id: unit1-hypervisors
tags: [virtualization, hypervisor, type-1-hypervisor, type-2-hypervisor, bare-metal, hosted, unit1]
aliases: [Hypervisor Types, Bare-Metal Hypervisor, Hosted Hypervisor]
links: ["[[00_Syllabus]]", "[[01_Unit_I_Intro_and_Cloud]]", "[[02_Unit_I_Need_for_Virtualization]]", "[[03_Unit_I_Limitations_of_Virtualization]]", "[[04_Unit_I_Types_of_Hardware_Virtualization]]"]
---

# Unit I: Types of Hypervisors

## 1.5 Types of Hypervisors

A **hypervisor**, also known as a **Virtual Machine Monitor (VMM)**, is the core software that creates and runs virtual machines (VMs). It's the essential layer that enables virtualization by abstracting the guest operating systems from the underlying hardware. There are two main types of hypervisors: Type-1 (Bare-Metal) and Type-2 (Hosted).

### What Does a Hypervisor Do?

The primary functions of a hypervisor include:
*   **Virtual Machine Creation and Management:** Allocating physical resources (CPU, RAM, storage) to VMs.
*   **Resource Scheduling:** Managing how VMs share physical resources and arbitrating access.
*   **Isolation:** Ensuring that one VM's activities do not interfere with another's.
*   **Emulation/Virtualization:** Translating VM requests to physical hardware (in Full Virtualization) or directing them via hardware assistance/paravirtualization.

### Type-1 Hypervisor (Bare-Metal or Native Hypervisor)

1.  **Concept:** A Type-1 hypervisor runs directly on the host computer's hardware, without an underlying operating system. It has direct access to the hardware resources, making it very efficient and powerful.
2.  **Architecture:** It sits directly on top of the physical hardware. Guest operating systems then run on top of the hypervisor.
3.  **Characteristics:**
    *   **High Performance:** Direct hardware access minimizes overhead.
    *   **High Security:** Less attack surface because there's no host OS to compromise.
    *   **Scalability:** Designed for managing large numbers of VMs in production environments.
    *   **Complex Management:** Often requires a separate management console or client (e.g., vSphere Client for VMware ESXi).
4.  **Analogy:** Imagine a building manager who lives in the building (the physical hardware) and directly manages all the apartments (VMs). They have full control and can allocate resources optimally.
5.  **Examples:** VMware ESXi, Microsoft Hyper-V, Citrix XenServer (now Citrix Hypervisor), KVM (Kernel-based Virtual Machine, technically a hybrid but often categorized as Type-1 for its bare-metal efficiency).

**ASCII Diagram: Type-1 Hypervisor**

```
+------------------------------------+
|  Guest OS 1  |  Guest OS 2  |  ... |
+------------------------------------+
|         TYPE-1 HYPERVISOR          |
+------------------------------------+
|          PHYSICAL HARDWARE         |
+------------------------------------+
```

### Type-2 Hypervisor (Hosted Hypervisor)

1.  **Concept:** A Type-2 hypervisor runs as an application on top of an existing operating system (the "host OS").
2.  **Architecture:** It relies on the host OS to handle hardware operations. The hypervisor itself runs as a process within the host OS, and guest operating systems then run on top of the hypervisor.
3.  **Characteristics:**
    *   **Ease of Use:** Simple to install and manage, often used for personal computers or development environments.
    *   **Lower Performance:** Performance can be impacted by the host OS, as both the host OS and the hypervisor compete for resources and add layers of abstraction.
    *   **Dependent on Host OS:** If the host OS crashes, all VMs running on it also crash.
    *   **Lower Security:** Larger attack surface due to the presence of a full host OS beneath the hypervisor.
4.  **Analogy:** Imagine an app on your computer that lets you run other apps in isolated environments. The computer's operating system is still managing everything, and the app is just another program it runs.
5.  **Examples:** VMware Workstation, VMware Fusion, Oracle VirtualBox, Parallels Desktop.

**ASCII Diagram: Type-2 Hypervisor**

```
+------------------------------------+
|  Guest OS 1  |  Guest OS 2  |  ... |
+------------------------------------+
|         TYPE-2 HYPERVISOR          |
+------------------------------------+
|             HOST OS                |
+------------------------------------+
|          PHYSICAL HARDWARE         |
+------------------------------------+
```

### Key Differences and Use Cases

| Feature          | Type-1 Hypervisor (Bare-Metal)                | Type-2 Hypervisor (Hosted)                   |
|------------------|-----------------------------------------------|----------------------------------------------|
| **Location**     | Runs directly on hardware                     | Runs as an application on a host OS          |
| **Performance**  | High (direct hardware access)                 | Lower (host OS overhead)                     |
| **Security**     | High (minimal attack surface)                 | Lower (depends on host OS security)          |
| **Complexity**   | More complex to set up/manage                 | Simpler to install and use                   |
| **Common Use**   | Production data centers, enterprise servers, cloud infrastructure | Personal use, development, testing, desktop virtualization |
| **Examples**     | VMware ESXi, Hyper-V, XenServer, KVM          | VMware Workstation, VirtualBox, Parallels    |

> [!tip]
> **Exam Focus:** Be able to clearly differentiate between Type-1 and Type-2 hypervisors based on their architecture, performance characteristics, and typical use cases. KVM is a common point of confusion, remember it's often grouped with Type-1 due to its Linux kernel integration for bare-metal performance.

---
