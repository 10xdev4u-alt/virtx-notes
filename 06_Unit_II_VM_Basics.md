---
title: "Unit II: Virtual Machine Basics"
id: unit2-vm-basics
tags: [virtualization, vm, virtual-machine, unit2, server-virtualization]
aliases: [VM Basics, Virtual Machine Fundamentals]
links: ["[[00_Syllabus]]", "[[05_Unit_I_Types_of_Hypervisors]]"]
---

# Unit II: Virtual Machine Basics

Welcome to Unit II! Now that we have a strong foundation in virtualization concepts, let's dive deeper into the core component that makes it all work: the **Virtual Machine (VM)**.

## 2.1 What is a Virtual Machine?

A Virtual Machine (VM) is a **software-based emulation of a physical computer**. It runs on a physical "host" machine but behaves like a completely separate, independent computer with its own virtualized hardware components, including:

*   **Virtual CPU (vCPU):** A share of the physical CPU's processing power.
*   **Virtual RAM (vRAM):** A portion of the host's physical memory.
*   **Virtual Hard Disk:** A file (or set of files) on the host's physical storage that acts as the VM's hard drive.
*   **Virtual Network Interface Card (vNIC):** A virtual network adapter that allows the VM to communicate on a network.

Essentially, a VM is a complete, self-contained computing environment encapsulated within software.

**ASCII Diagram: VM Encapsulation**

This diagram illustrates how a VM is a self-contained package of files managed by the hypervisor.

```
+-------------------------------------------------+
|            VIRTUAL MACHINE (VM)                 |
|                                                 |
|  +-------------------------------------------+  |
|  |             Guest Operating               |  |
|  |          System (e.g., Windows)           |  |
|  +-------------------------------------------+  |
|  |     Applications (e.g., Web Server)       |  |
|  +-------------------------------------------+  |
|  |      Binaries / Libraries / Drivers       |  |
|  +-------------------------------------------+  |
|                                                 |
|  -- Encapsulated by the Hypervisor --           |
+-------------------------------------------------+
|                                                 |
|  Associated VM Files on Host Storage:           |
|  +--------------------------+                   |
|  |  my_vm.vmx (Config File) |                   |
|  +--------------------------+                   |
|  |  my_vm.vmdk (Virtual HD) |                   |
|  +--------------------------+                   |
|  |  my_vm.nvram (BIOS)      |                   |
|  +--------------------------+                   |
|                                                 |
+-------------------------------------------------+
```

### Key Characteristics of a Virtual Machine

1.  **Isolation:** VMs are strongly isolated from each other and from the host machine. A crash, security breach, or error in one VM does not affect other VMs on the same host. This is a critical security and stability feature.

2.  **Encapsulation:** An entire VM—including its hardware configuration, operating system, applications, and data—is encapsulated into a small set of files. This makes VMs incredibly portable.
    *   **Analogy:** Think of a VM as a detailed message in a bottle. The entire world (the OS, apps, data) is inside the bottle (the set of files). You can easily pick up this bottle and move it to another beach (another physical host) without changing its contents.

3.  **Hardware Independence:** Because the hypervisor abstracts the physical hardware, a VM can run on any physical host that supports the same hypervisor, regardless of the underlying hardware vendor (e.g., Dell, HP, etc.). This eliminates vendor lock-in and simplifies hardware upgrades.

4.  **Snapshots:** Hypervisors allow you to take a "snapshot" of a VM at a specific point in time. This captures the entire state of the VM—including its memory, disk, and configuration. Snapshots are invaluable for:
    *   **Testing:** Apply a patch or make a change. If something goes wrong, you can instantly revert the VM to the pre-change state.
    *   **Backups:** Provides a quick way to create a point-in-time backup before major operations.

> [!tip]
> **Exam Focus:** Be prepared to define a VM and explain its core characteristics: Isolation, Encapsulation, and Hardware Independence. Understand that a VM is not just an OS, but a complete, software-defined computer system.

---
