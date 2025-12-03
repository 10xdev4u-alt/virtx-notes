---
title: "Unit II, Topic 08: Types of Desktop Virtualization"
id: unit2-topic8-desktop-virt-types
tags:
  - unit2
  - desktop-virtualization
  - vdi
  - sbc
  - rds
  - client-hypervisor
aliases:
  - VDI Types
  - Desktop Virtualization Architectures
links:
  - "[[00_Syllabus]]"
  - "[[12_Unit_II_Topic07_Desktop_Virtualization_Intro]]"
  - "[[ClgMatx/SemVPrep/VirtX/Unit_02_Quiz]]"
---

# Unit II, Topic 08: Types of Desktop Virtualization

Desktop virtualization is not a one-size-fits-all solution. There are several distinct architectures for delivering virtual desktops, each with its own trade-offs in terms of cost, performance, and personalization.

## 1. Virtual Desktop Infrastructure (VDI)

This is the most common and comprehensive form of desktop virtualization.

-   **Concept:** Each user connects over a network to their own dedicated virtual machine, which is running a standard desktop operating system (like Windows 10), hosted on a centralized server in the data center.
-   **Architecture:**
    -   Uses a **Type-1 hypervisor** on powerful backend servers to host the desktop VMs.
    -   A **Connection Broker** is a critical component that acts as a traffic cop. It authenticates the user, checks their entitlements, and connects them to their assigned virtual desktop.
-   **Sub-types (as discussed previously):**
    -   **Persistent VDI:** Each user gets a unique, customizable VM. Best for power users and developers.
    -   **Non-Persistent VDI:** Users get a generic, fresh VM from a pool at each login. Best for task workers and standardized environments.
-   **Use Cases:** Large enterprises, secure remote access, environments with diverse user needs that can be met with both persistent and non-persistent desktops.
-   **Examples:** VMware Horizon, Citrix Virtual Desktops, Microsoft Azure Virtual Desktop (AVD).

## 2. Session-Based Computing (SBC) / Remote Desktop Services (RDS)

This is an older, but still very relevant and highly efficient, form of desktop delivery.

-   **Concept:** Multiple users **share a single, powerful server** that runs a multi-session-capable operating system (e.g., Windows Server). Each user gets their own isolated **session** within that single shared OS, not their own VM.
-   **Architecture:** Does not use hypervisors in the same way as VDI. It relies on the OS's ability to handle multiple concurrent user sessions.
-   **Key Difference:** In VDI, 10 users would mean 10 separate Windows 10 VMs, each with its own OS instance. In SBC, 10 users would mean 10 sessions running on **one** Windows Server OS instance.
-   **Use Cases:**
    -   Delivering a small, standardized set of applications to many users.
    -   Task-worker environments where personalization is not required.
    -   Cost-sensitive environments where maximizing server density is the top priority.
-   **Pros:**
    -   **High Efficiency:** Very high user density per server, leading to lower hardware costs.
    -   **Simple Management:** Only one server OS and application set to patch and manage.
-   **Cons:**
    -   **Limited Personalization:** All users share the same OS and applications.
    -   **Application Compatibility:** Some applications may not work correctly in a multi-session environment.
    -   **Weaker Isolation:** A problem with the shared OS can potentially impact all users connected to it (the "noisy neighbor" problem is more pronounced).
-   **Examples:** Microsoft Remote Desktop Services (RDS), Citrix Virtual Apps.

## 3. Client-Side (or Local) Hypervisor

This approach flips the model and brings the virtualization back to the user's local device.

-   **Concept:** A **Type-2 hypervisor** (like VirtualBox or VMware Workstation) runs on the user's physical endpoint device (e.g., their laptop). The virtual machine, containing the corporate desktop, runs directly on the user's local hardware.
-   **Architecture:** The VM's OS and applications reside locally on the user's machine, not in the data center.
-   **Use Cases:**
    -   Developers who need to run different operating systems or test environments.
    -   Mobile users or contractors who need to work **offline** but still require a secure, managed corporate desktop.
    -   Creating a secure, sandboxed "corporate" environment on an employee's personal laptop (a BYOD scenario).
-   **Pros:**
    -   **Offline Access:** The VM can be used without a network connection.
    -   **High Performance:** Leverages local hardware, so there is no network latency.
    -   **Uses Local Peripherals:** Easily interacts with the user's local devices.
-   **Cons:**
    -   **Decentralized Management:** IT has less control, as the VM resides on the user's device.
    -   **Data Security:** The corporate data is now stored on the user's endpoint device, re-introducing the risk of data loss from stolen or lost laptops (though the VM can be encrypted).

## Summary Table: Desktop Virtualization Types

| Feature             | VDI (Server-Side)                               | SBC / RDS (Server-Side)                         | Client-Side Hypervisor (Local)                  |
|---------------------|-------------------------------------------------|-------------------------------------------------|-------------------------------------------------|
| **Resource Unit**   | One VM per user                                 | One Session per user (on a shared OS)           | One VM per user (on their own device)           |
| **Isolation**       | High (OS-level)                                 | Lower (Session-level)                           | High (OS-level)                                 |
| **Personalization** | High (especially with Persistent VDI)           | Low                                             | High                                            |
| **Resource Usage**  | High                                            | Very Low (most efficient)                       | Uses local device resources                     |
| **Offline Access**  | No                                              | No                                              | **Yes**                                         |
| **Use Case**        | Personalized desktops, secure remote access     | Task workers, application publishing            | Developers, offline/mobile workers              |
| **Examples**        | VMware Horizon, Citrix Virtual Desktops         | Microsoft RDS, Citrix Virtual Apps              | VirtualBox, VMware Workstation                  |

> [!success] **Exam Focus**
> - **6-Mark Question:** "Compare VDI and Session-Based Computing (SBC)."
>   - **Answer Strategy:** The key difference is the resource unit: VDI is **one VM per user**, while SBC is **one session per user on a shared OS**. From this, you can derive the other differences. VDI has higher isolation and personalization but is more resource-intensive. SBC is more resource-efficient and simpler to manage but offers less isolation and personalization.
> - **4-Mark Question:** "Describe a scenario where a client-side hypervisor is the most appropriate desktop virtualization solution."
>   - **Answer:** Describe a scenario involving a user who needs to work while disconnected from the network, such as a traveling consultant or a field engineer. They need a secure, managed corporate desktop environment on their laptop that they can use offline. A client-side hypervisor (like VMware Workstation) allows them to run the corporate VM locally, providing both offline capability and isolation from their personal laptop OS.
