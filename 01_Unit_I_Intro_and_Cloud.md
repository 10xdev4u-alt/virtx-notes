---
title: "Unit I: Introduction to Virtualization and Cloud Computing"
id: unit1-intro-cloud
tags: [virtualization, cloud-computing, unit1]
aliases: [Intro to Virtualization, Virtualization Basics, Cloud Computing Basics]
links: ["[[00_Syllabus]]", "[[02_Unit_I_Need_for_Virtualization]]"]
---

# Unit I: Introduction to Virtualization and Cloud Computing

## 1.1 Virtualization and Cloud Computing

### What is Virtualization?

At its core, **virtualization** is the technology used to create a virtual (rather than actual) version of something, including virtual computer hardware platforms, storage devices, and computer network resources. It is about abstracting resources.

In simple terms, virtualization software allows you to run multiple, independent, and isolated operating systems on a single physical computer. Each of these isolated environments is called a **Virtual Machine (VM)**. From the perspective of the applications and the operating system inside the VM, it appears to be a real, physical machine with its own dedicated hardware (CPU, RAM, storage, network card).

**ASCII Diagram: Visualizing Virtualization**

This diagram shows one physical server running three virtual machines. The **Hypervisor** is the key software layer that enables this.

```
+-----------------------------------------------------+
|        Virtual Machine 3 (e.g., Ubuntu Linux)       |
| +-----------------+  +-------------+  +-----------+ |
| |   Application   |  |  Guest OS   |  | Virtual   | |
| |      (Web      |  |   (Ubuntu)  |  | Hardware  | |
| |     Server)    |  |             |  | (vCPU,    | |
| +-----------------+  +-------------+  | vRAM...)  | |
+--------------------|------------------+-----------+--+
                     |
+--------------------|------------------+-----------+--+
|        Virtual Machine 2 (e.g., Windows Server)     |
| +-----------------+  +-------------+  +-----------+ |
| |   Application   |  |  Guest OS   |  | Virtual   | |
| |   (Database)    |  |  (Windows)  |  | Hardware  | |
| +-----------------+  +-------------+  +-----------+ |
+--------------------|-------------------------------+
                     |
+--------------------|-------------------------------+
|        Virtual Machine 1 (e.g., CentOS)           |
| +-----------------+  +-------------+  +-----------+ |
| |   Application   |  |  Guest OS   |  | Virtual   | |
| |      (App      |  |   (CentOS)  |  | Hardware  | |
| |     Server)    |  |             |  +-----------+ |
| +-----------------+  +-------------+                |
+-----------------------------------------------------+
|                  HYPERVISOR                         |
|      (Virtualization Layer - e.g., VMWare ESXi)     |
+-----------------------------------------------------+
|                  PHYSICAL HARDWARE                  |
| +-----------+  +-----------+  +---------+  +------+ |
| |    CPU    |  |    RAM    |  | Storage |  |  NIC | |
| +-----------+  +-----------+  +---------+  +------+ |
+-----------------------------------------------------+
         << Physical Server >>
```

**Analogy: The Office Building (Revisited)**
- **Physical Server:** A large, empty office building.
- **Hypervisor:** The building's management and infrastructure team. They install the plumbing, electricity, and framework that allows for separate office suites to exist.
- **Virtual Machines (VMs):** The individual, secure office suites. Each has its own metered electricity, water, and a keycard-access door (representing allocated CPU, RAM, and isolated security). A company in one suite can be a design firm, the one next door a law office—they operate independently, unaware of each other's activities.

### The Relationship with Cloud Computing

Virtualization is the **enabling technology** that makes cloud computing a reality. Cloud computing is a **service model** that delivers these virtualized resources over the Internet.

| Feature         | Virtualization                                       | Cloud Computing                                           |
|-----------------|------------------------------------------------------|-----------------------------------------------------------|
| **Core Idea**   | Technology that creates virtual resources from physical hardware. | Service model for delivering computing resources on-demand. |
| **Scope**       | Focused on creating VMs and managing hypervisors.    | Broader scope: includes servers, storage, databases, networking, software. |
| **Key Element** | The **Hypervisor** (software).                       | The **Internet** (delivery mechanism) and **APIs** (for management). |
| **Example**     | Running two VMs (Windows and Linux) on your personal laptop using VirtualBox. | Using Amazon Web Services (AWS) to launch a server for your website, without ever touching the physical hardware. |

> [!note]
> **Key Relationship:** Virtualization is the *engine*. Cloud Computing is the *car* you drive. The engine (virtualization) makes the car work by creating usable power from fuel. The car (cloud) provides the controls, seats, and wheels to deliver that power as a useful service (transportation).
