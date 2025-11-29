---
title: "Unit II: Types of Virtual Machines"
id: unit2-types-of-vms
tags: [virtualization, vm, virtual-machine-types, unit2, server-virtualization]
aliases: [VM Types, Types of VMs]
links: ["[[00_Syllabus]]", "[[06_Unit_II_VM_Basics]]"]
---

# Unit II: Types of Virtual Machines

Now that we understand what a Virtual Machine (VM) is and its core characteristics, let's explore the various types of VMs you might encounter. While the fundamental concept remains the same, VMs can be categorized based on their purpose or how they are provisioned and managed.

## 2.2 Types of Virtual Machines

The categorization of VMs can vary slightly depending on the context, but generally, we can look at them from several angles.

### By Operating System & Workload

1.  **Server VMs:**
    *   **Purpose:** Designed to host server-side applications and services. This includes web servers (Apache, Nginx), database servers (MySQL, PostgreSQL), application servers (Java EE, .NET), email servers, and other backend services.
    *   **Characteristics:** Typically configured with more vCPUs and vRAM, often optimized for performance and stability for continuous operation. They are the backbone of data centers and cloud infrastructure.
    *   **Examples:** A Linux VM running a corporate website, a Windows Server VM hosting an Exchange email server.

2.  **Desktop VMs:**
    *   **Purpose:** Used to provide virtualized desktop environments for end-users. This can be for remote access, secure workstations, or providing a standard desktop image to many users.
    *   **Characteristics:** Often configured with fewer resources than server VMs, but optimized for user interaction (graphics, peripherals). Key to technologies like Virtual Desktop Infrastructure (VDI).
    *   **Examples:** A Windows 10 VM accessed remotely by an employee, a Linux VM used for specific development tasks.

3.  **Appliance VMs:**
    *   **Purpose:** Pre-configured VMs designed for a specific function or application. They are typically distributed as a single package (e.g., OVF, OVA) ready to deploy.
    *   **Characteristics:** Simplified deployment, often requires minimal configuration, and can encapsulate an entire software stack (OS + application).
    *   **Examples:** A virtual firewall appliance, a pre-packaged CRM solution, a network monitoring tool distributed as a VM.

### By Deployment/Management Model

1.  **Persistent VMs:**
    *   **Concept:** Each user has their own dedicated VM, and all changes made by the user (installing applications, saving files, changing settings) are saved and persist across sessions.
    *   **Use Case:** Ideal for power users, developers, or anyone who needs a personalized and customizable desktop environment.
    *   **Pros:** Familiar user experience, high personalization.
    *   **Cons:** Requires more storage, more complex to manage updates and patches across many unique VMs.

2.  **Non-Persistent (or Stateless) VMs:**
    *   **Concept:** Users are assigned a fresh VM from a pool each time they log in. Any changes made by the user (installing applications, saving files, changing settings) are discarded upon logout or reboot. User data is typically stored separately (e.g., on a network drive or in a profile management system).
    *   **Use Case:** Common in call centers, public access terminals, or environments where a standardized, secure, and easily refreshable desktop is needed.
    *   **Pros:** Easy to manage (patch the golden image once), enhanced security (fresh session every time).
    *   **Cons:** Limited personalization, requires separate user profile management.

### Specialized VMs

1.  **Test/Development VMs:**
    *   **Purpose:** Used by developers and testers to create isolated environments for building, testing, and debugging software.
    *   **Characteristics:** Can be easily cloned, reverted via snapshots, and deleted without impacting production systems.

2.  **Disaster Recovery (DR) VMs:**
    *   **Purpose:** Replicas of production VMs maintained in a separate location, ready to be activated in case of a disaster affecting the primary data center.
    *   **Characteristics:** Often kept in a powered-off state or with minimal resources until needed.

> [!tip]
> **Exam Focus:** Understand the distinction between Server VMs and Desktop VMs based on their purpose and resource allocation. Be able to explain the difference between Persistent and Non-Persistent VMs, especially in the context of VDI.

---
