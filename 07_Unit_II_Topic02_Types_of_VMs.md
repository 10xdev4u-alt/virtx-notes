---
title: "Unit II, Topic 02: Types of Virtual Machines"
id: unit2-topic2-vm-types
tags:
  - unit2
  - virtualization
  - vm
  - virtual-machine-types
aliases:
  - VM Types
  - Types of VMs
links:
  - "[[00_Syllabus]]"
  - "[[06_Unit_II_Topic01_VM_Basics]]"
  - "[[08_Unit_II_Topic03_Server_Virtualization_Intro]]"
---

# Unit II, Topic 02: Types of Virtual Machines

While the underlying technology of a Virtual Machine is consistent, VMs can be categorized based on their purpose, workload, or management model. Understanding these distinctions is key to deploying the right kind of virtual resource for a specific task.

## 2.2.1 Categorization by Workload

This is the most common way to classify VMs, based on the job they are intended to perform.

### 1. Server VMs
-   **Purpose:** These are the workhorses of the data center, designed to host server-side applications and services that run 24/7.
-   **Workloads:** Web servers (Apache, Nginx), database servers (MySQL, SQL Server), application servers (Java, .NET), email servers (Exchange), Active Directory controllers, and other backend services.
-   **Characteristics:**
    -   Typically configured with significant vCPU and vRAM resources.
    -   Optimized for performance, stability, and high availability.
    -   Often have minimal graphical user interfaces (GUIs) or run in a "headless" state.
-   **Example:** A Linux VM running a corporate website, or a Windows Server VM hosting a critical business database.

### 2. Desktop VMs
-   **Purpose:** Used to provide a complete, interactive desktop environment to an end-user. This is the foundation of **Virtual Desktop Infrastructure (VDI)**.
-   **Workloads:** Standard office applications (Microsoft Office), web browsers, custom client-server applications, and development environments.
-   **Characteristics:**
    -   Often configured with fewer vCPU/vRAM resources than server VMs.
    -   Optimized for user interaction, including responsive graphics, audio, and peripheral support (USB, printers).
-   **Example:** A Windows 10 VM accessed remotely by an employee, allowing them to work from any device.

### 3. Appliance VMs
-   **Purpose:** A pre-configured, pre-packaged, "turnkey" VM designed to perform a single, specific function. They are distributed as a ready-to-deploy package (often in OVF or OVA format).
-   **Workloads:** Network firewalls, VPN gateways, load balancers, network monitoring tools, or even entire application stacks like a pre-installed CRM.
-   **Characteristics:**
    -   **Simplified Deployment:** Requires minimal configuration from the end-user.
    -   **Self-Contained:** Encapsulates the entire software stack (OS + application) needed for its function.
-   **Example:** A virtual firewall appliance from a security vendor that you can download and run on your hypervisor to protect your virtual network.

## 2.2.2 Categorization by Deployment Model (Primarily for VDI)

This categorization is most relevant in the context of desktop virtualization.

### 1. Persistent VMs
-   **Concept:** Each user is assigned their own dedicated virtual desktop. All changes made by the user—installing applications, saving files to the desktop, changing wallpaper, modifying settings—are **saved and persist** across sessions.
-   **User Experience:** It feels exactly like a personal physical desktop.
-   **Use Case:** Ideal for "power users," developers, executives, and anyone who needs a highly personalized and customizable desktop environment.
-   **Pros:** High degree of personalization and a familiar user experience.
-   **Cons:**
    -   **Higher Storage Cost:** Each VM is unique, consuming more storage space.
    -   **Complex Management:** Managing updates and patches is difficult, as each of the hundreds or thousands of desktops is a unique entity.

### 2. Non-Persistent (or Stateless) VMs
-   **Concept:** Users are assigned a generic, fresh VM from a pool each time they log in. Any changes made during the session are **discarded** upon logout or reboot. The VM reverts to its original, pristine "golden image" state.
-   **User Experience:** Standardized and locked-down. User-specific data is typically stored on a separate network drive or managed via a profile management solution.
-   **Use Case:** Excellent for task-based workers like call center agents, public access terminals (libraries, kiosks), or training labs where a consistent, secure, and easily refreshable desktop is required.
-   **Pros:**
    -   **Simplified Management:** To patch or update all desktops, you only need to update the single "golden image."
    -   **Enhanced Security:** Every session starts from a clean, known-good state, eliminating malware or misconfigurations from previous sessions.
    -   **Lower Storage Cost:** Requires significantly less storage as it leverages linked-clone technology.
-   **Cons:** Limited personalization and requires a separate solution for managing user profiles and data.

> [!success] **Exam Focus**
> - **4-Mark Question:** "Distinguish between Server VMs and Desktop VMs."
>   - **Answer Strategy:** Focus on their **Purpose** and **Characteristics**. Server VMs are for backend services, optimized for performance and stability with high resource allocation. Desktop VMs are for end-user interaction, optimized for graphical responsiveness with typically lower resource allocation.
> - **6-Mark Question:** "Compare and contrast Persistent and Non-Persistent VDI."
>   - **Answer Strategy:** This is a classic VDI question. Create a table or use bullet points.
>     - **User Changes:** Saved in Persistent, Discarded in Non-Persistent.
>     - **Personalization:** High in Persistent, Low in Non-Persistent.
>     - **Management:** Complex in Persistent, Simple in Non-Persistent (update one golden image).
>     - **Storage:** High in Persistent, Low in Non-Persistent.
>     - **Use Case:** Power users/developers for Persistent, Task workers/call centers for Non-Persistent.
