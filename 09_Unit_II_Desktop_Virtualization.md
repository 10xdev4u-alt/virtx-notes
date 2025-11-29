---
title: "Unit II: Desktop Virtualization"
id: unit2-desktop-virtualization
tags: [virtualization, desktop-virtualization, vdi, sbc, client-hypervisor, unit2]
aliases: [VDI, Types of Desktop Virtualization]
links: ["[[00_Syllabus]]", "[[06_Unit_II_VM_Basics]]", "[[07_Unit_II_Types_of_VMs]]", "[[08_Unit_II_Server_Virtualization]]"]
---

# Unit II: Desktop Virtualization

Having explored server virtualization, let's now shift our focus to **Desktop Virtualization**, which provides flexible and secure ways to deliver desktop environments to end-users.

## 2.4 Desktop Virtualization

**Desktop Virtualization** is the process of separating the desktop environment and associated application software from the physical client device that is used to access it. Essentially, the user's desktop operating system and applications run on a centralized server (or a local hypervisor), and only the screen, keyboard, and mouse inputs/outputs are transmitted to the user's device.

### Key Drivers for Desktop Virtualization

1.  **Enhanced Security:** Centralizing desktops on servers makes data more secure. Data never leaves the data center, reducing risks from lost or stolen devices. Updates and patches are applied once to a central image.
2.  **Simplified Management:** IT can manage all desktops from a central console, simplifying provisioning, patching, and application deployment.
3.  **Increased Mobility & Flexibility:** Users can access their personalized desktop from any device, anywhere, anytime, promoting remote work and BYOD (Bring Your Own Device) initiatives.
4.  **Cost Savings:** While initial setup can be costly, long-term operational costs can be reduced through easier management and extended lifespan of client devices (thin clients).
5.  **Business Continuity & Disaster Recovery:** Desktops are not tied to physical hardware, making them easier to restore and recover in case of device failure or disaster.

### Types of Desktop Virtualization

Desktop virtualization can be implemented in several ways, each with its own architecture and use cases.

1.  **Virtual Desktop Infrastructure (VDI):**
    *   **Concept:** This is the most common form of desktop virtualization. Each user gets a dedicated VM (or is assigned one from a pool) running on a centralized server. The user connects to their VM over a network.
    *   **Architecture:** Typically uses a Type-1 hypervisor on powerful backend servers. A connection broker manages user sessions and connects users to their assigned or available VMs.
    *   **Use Cases:** Large enterprises, call centers, users needing personalized and persistent desktops, secure remote access.
    *   **Sub-types within VDI:**
        *   **Persistent VDI:** Each user has a unique VM. Changes are saved. (Similar to Persistent VMs discussed earlier).
        *   **Non-Persistent VDI:** Users get a fresh VM from a pool at each login. Changes are discarded. (Similar to Non-Persistent VMs).
    *   **Examples:** VMware Horizon, Citrix Virtual Apps and Desktops, Microsoft Remote Desktop Services (RDS) with Hyper-V.

2.  **Session-Based Computing (SBC) / Remote Desktop Services (RDS):**
    *   **Concept:** Multiple users share a single, powerful server that runs the desktop OS and applications. Each user gets their own isolated session within the shared OS.
    *   **Architecture:** Desktops are not separate VMs, but individual user sessions on one shared OS (e.g., Windows Server's Remote Desktop Session Host).
    *   **Use Cases:** Task workers, users with standard application needs, cost-sensitive environments, delivering specific applications remotely.
    *   **Pros:** Very efficient use of server resources, lower storage requirements than VDI.
    *   **Cons:** Limited personalization, one user can potentially impact others, not suitable for applications that require isolation at the OS level.
    *   **Examples:** Microsoft Remote Desktop Services (RDS), Citrix Virtual Apps.

3.  **Client-Side (or Local) Hypervisor:**
    *   **Concept:** A Type-2 hypervisor runs on the user's local endpoint device (laptop, desktop). The VM runs directly on the user's hardware.
    *   **Architecture:** Uses a hosted hypervisor. The VM's OS and applications reside locally.
    *   **Use Cases:** Developers, mobile users who need to work offline, users requiring specific OSes not native to their device, secure sandboxed environments.
    *   **Pros:** Offline access, better performance (no network latency), leverages local hardware.
    *   **Cons:** Management burden (each client device must be managed), security of the local device is paramount.
    *   **Examples:** VMware Workstation, Oracle VirtualBox, Parallels Desktop.

> [!summary]
> Desktop virtualization provides centralized management, enhanced security, and greater flexibility for end-users by decoupling the desktop environment from the physical device. VDI is the most comprehensive approach, while SBC/RDS offers resource efficiency, and client-side hypervisors provide local performance and offline access.

---
