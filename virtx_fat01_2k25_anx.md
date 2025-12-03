---
title: "FAT01 - CS22051 Virtualization Techniques (2k25) - Answer Key"
id: virtx-fat01-2k25-anx
tags:
  - fat-answers
  - virtualization
  - unit1
  - unit2
aliases:
  - FAT01 2k25 Answers
links:
  - "[[virt_fat01_2k25]]"
---

# FAT01 - CS22051 Virtualization Techniques (2k25) - Answer Key

Here are the detailed answers for the First Assessment Test (FAT) of the 2k25 series on Virtualization Techniques.

---

## PART A (10 x 2 = 20 Marks)

**1. Describe about Cloud Computing.**

Cloud Computing is a service model for delivering on-demand computing services—including servers, storage, databases, networking, and software—over the Internet ("the cloud"). It relies on virtualization to pool and abstract resources, offering key characteristics like on-demand self-service, broad network access, resource pooling, rapid elasticity, and measured service.

**2. Discuss about the limitations of virtualization.**

The main limitations of virtualization include:
-   **Performance Overhead:** The hypervisor itself consumes some hardware resources, meaning a VM will never be quite as fast as a native physical machine.
-   **Increased Complexity:** It introduces a new layer of management for hypervisors, virtual networks, and shared storage.
-   **Single Point of Failure:** The physical host server becomes a critical point of failure; if it goes down, all VMs on it go down.
-   **Resource Contention:** Multiple VMs compete for the same physical CPU, RAM, and I/O, which can lead to performance degradation.

**3. Define virtualization and state its need in the context of cost reduction.**

**Definition:** Virtualization is the process of creating a virtual (software-based) version of a physical resource, such as a server, storage device, or network.

**Need for Cost Reduction:** The primary need for virtualization arose from the inefficiency of the "one app, one server" model, which led to server sprawl and massive underutilization of hardware. Virtualization enables **server consolidation**, allowing many VMs to run on a single physical server. This drastically reduces costs by lowering hardware procurement, power consumption, cooling expenses, and data center space requirements.

**4. Who are the leading cloud service providers? Justify.**

The three leading cloud service providers are:
1.  **Amazon Web Services (AWS):** The market leader. Justified by its early entry, massive global infrastructure, and the most extensive portfolio of services.
2.  **Microsoft Azure:** The second largest provider. Justified by its strong enterprise presence, seamless integration with Microsoft products, and robust hybrid cloud offerings.
3.  **Google Cloud Platform (GCP):** The third major player. Justified by its strength in networking, data analytics, machine learning, and containerization (Kubernetes).

**5. List out the types of hypervisors with an example.**

1.  **Type-1 Hypervisor (Bare-Metal):** Runs directly on the host's physical hardware.
    -   *Example:* VMware ESXi, Microsoft Hyper-V.
2.  **Type-2 Hypervisor (Hosted):** Runs as an application on top of a conventional operating system.
    -   *Example:* Oracle VM VirtualBox, VMware Workstation.

**6. Describe the virtual machine.**

A Virtual Machine (VM) is a software-based emulation of a physical computer. It is a fully self-contained and isolated computing environment that runs its own operating system and applications by using a share of the physical host's resources (CPU, RAM, storage), which are managed by a hypervisor.

**7. Mention the distinctions between virtual machine and physical machine.**

-   **Abstraction:** A VM is a software abstraction encapsulated in files, while a physical machine is tangible hardware.
-   **Portability:** A VM is highly portable and can be easily moved or copied between physical hosts. A physical machine is tied to its hardware.
-   **Resource Management:** A VM uses virtualized resources managed by a hypervisor. A physical machine has direct control over its hardware resources.
-   **Provisioning:** A VM can be provisioned in minutes, while a physical machine takes days or weeks to procure and set up.

**8. What is the use of virtual machine and its significance in server virtualization concept?**

**Use:** The use of a virtual machine is to provide an isolated, software-defined computing environment that can run an operating system and applications.
**Significance:** In server virtualization, the VM is the fundamental unit of consolidation. The concept's significance lies in enabling multiple VMs to run on a single physical server, which is the core mechanism for achieving higher hardware utilization, reducing server sprawl, and lowering costs.

**9. Interpret various benefits of server virtualization.**

The primary benefits of server virtualization are:
-   **Server Consolidation:** Reduces the number of physical servers, leading to cost savings.
-   **Increased Hardware Utilization:** Maximizes the use of expensive server hardware.
-   **Faster Provisioning:** New servers (VMs) can be deployed in minutes.
-   **Improved Disaster Recovery:** VMs are easy to back up, replicate, and restore, enhancing business continuity.
-   **Simplified Management:** Centralized tools allow for easier management of many servers.

**10. Write the working of hardware virtualization and challenges posted.**

**Working:** Hardware virtualization works by using a software layer called a hypervisor to abstract the physical hardware of a host machine. The hypervisor presents this abstracted hardware to multiple guest operating systems (in VMs), managing their access to the physical CPU, memory, and I/O to ensure they remain isolated from one another. Modern systems use CPU extensions (Intel VT-x/AMD-V) to accelerate this process.

**Challenges:**
-   **Performance Overhead:** The hypervisor's management activities consume resources.
-   **Complexity:** Managing the virtual layer is more complex than managing standalone physical servers.
-   **Resource Contention:** VMs can compete for shared physical resources, potentially causing bottlenecks.

---

## PART B (3 x 10 = 30 Marks)

**11. (a) Discuss about full virtualization, partial virtualization and para virtualization to a real-world example of virtualization deployment. Analyze the suitability of each type of virtualization for different use cases.**

**Hardware Virtualization Types:**

1.  **Full Virtualization:**
    -   **Discussion:** In full virtualization, the hypervisor completely emulates the underlying hardware, allowing an unmodified guest OS to run without any awareness that it is being virtualized. It uses a technique called "trap-and-emulate" or binary translation to handle sensitive instructions.
    -   **Suitability:** Its key advantage is compatibility. It is suitable for:
        -   Running proprietary, closed-source operating systems like **Microsoft Windows**, where the kernel cannot be modified.
        -   Virtualizing **legacy applications** running on older, unsupported operating systems to move them to modern hardware.

2.  **Paravirtualization (PV):**
    -   **Discussion:** In paravirtualization, the guest OS is modified to be "aware" of the hypervisor. Instead of trying to execute privileged instructions, it makes direct API calls ("hypercalls") to the hypervisor. This cooperative approach eliminates the overhead of trap-and-emulate, leading to better performance.
    -   **Suitability:** Its key advantage is performance. It is suitable for:
        -   High-performance computing environments where every bit of performance matters.
        -   Virtualizing **open-source operating systems like Linux**, where the kernel can be freely modified to include the necessary drivers and hypercall capabilities.

3.  **Partial Virtualization:**
    -   **Discussion:** This is an older and less common term. It describes systems where only some, but not all, of the hardware is virtualized (e.g., address space or CPU virtualization, but not I/O). The guest OS is aware it is in a virtual environment and some modification may be required. It does not provide the complete isolation of full virtualization.
    -   **Suitability:** This concept has been largely superseded by modern **Hardware-Assisted Virtualization (HVM)**. Its historical use cases, like running multiple applications in separate virtual memory spaces, are now better handled by modern OS features or full HVM.

**Real-World Example & Analysis:**

Consider a company deploying a new data center.
-   They would use **Hardware-Assisted Virtualization** (the modern evolution of Full Virtualization) for the majority of their workloads, including their **Windows Server** virtual machines, because it offers high compatibility without requiring OS modification.
-   For a high-performance, custom **Linux-based** data analytics cluster, they might have historically considered **Paravirtualization** to squeeze out maximum performance. However, today's HVM is so efficient that PV is less common, but the principle of using optimized drivers (PV drivers) in HVM environments remains.
-   **Partial Virtualization** would not be used, as it doesn't provide the complete, secure server isolation required for a modern data center.

**(OR)**

**11. (b) Provide a case study where 'n' company implemented virtualization to reduce infrastructure costs. Evaluate the benefits and limitations of virtualization in this scenario.**

**Case Study: "Innovate Corp" Cost Reduction through Virtualization**

**Scenario:**
Innovate Corp, a mid-sized software company, had a data center with 40 physical servers. Each server was dedicated to a single function: web server, database, source control, testing environment, etc. An audit revealed that the average CPU utilization across these servers was only 12%. The company was facing high operational costs from power, cooling, and data center space, and needed to buy new servers for an upcoming project.

**Implementation:**
Innovate Corp decided to implement a server virtualization project using VMware vSphere.
1.  They purchased 3 powerful new physical servers with multi-core CPUs and large amounts of RAM.
2.  They used VMware's P2V (Physical-to-Virtual) converter tool to migrate the 40 existing physical workloads into 40 virtual machines.
3.  These 40 VMs were consolidated onto the 3 new physical hosts.

**Evaluation of Benefits:**

1.  **Drastic Cost Reduction:**
    -   **Capital Expense (CapEx) Avoidance:** They did not have to buy new servers for the upcoming project. Instead, they just provisioned new VMs on the existing hosts.
    -   **Operational Expense (OpEx) Reduction:** By decommissioning 37 old physical servers (40 original - 3 new), they saw an immediate and significant drop in their monthly electricity bill (for power and cooling) and were able to free up several server racks in their data center.
2.  **Increased Resource Utilization:** The 3 new hosts ran at an average of 70% CPU utilization, a massive improvement from the previous 12%. This ensured they were getting maximum value from their hardware investment.
3.  **Increased Agility:** When the development team needed 5 new test servers, the IT team was able to provision them as VMs in under an hour, a process that previously would have taken weeks to procure and set up physical hardware.

**Evaluation of Limitations Encountered:**

1.  **Performance Bottleneck (A Limitation in Practice):** During the initial migration, they placed two I/O-heavy database VMs on the same host, which created a storage performance bottleneck for all VMs on that host. They had to rebalance the VMs, moving one database to a different host to resolve the issue. This highlighted the challenge of **resource contention**.
2.  **Increased Complexity (A Limitation in Management):** The IT team, used to managing individual servers, had to learn how to manage a more complex environment with vCenter, shared storage, and virtual networking. This required an initial investment in **staff training**.
3.  **Single Point of Failure (A Limitation in Design):** They realized that if one of the 3 new hosts failed, the ~13 VMs on it would go down. This forced them to properly configure **VMware High Availability (HA)** to mitigate this risk, adding to the initial setup complexity.

**12. (a) An enterprise is planning to virtualize its data center to improve resource utilization and system performance. The IT team is considering paravirtualization as an approach and wants to understand how it works in real-world environments. They are particularly interested in Xen architecture, which is commonly used for implementing paravirtualization. Explain how paravirtualization works and discuss the Xen architecture in detail, highlighting its components, functionality, and role in improving virtualization performance.**

**How Paravirtualization Works:**

Paravirtualization is a virtualization technique where the guest operating system is modified to be "aware" that it is a VM running on a hypervisor. Instead of the hypervisor trying to trick the guest OS, the two cooperate. The guest OS kernel is modified to replace its privileged, hardware-sensitive instructions with direct API calls to the hypervisor, known as **hypercalls**. This eliminates the performance overhead associated with the "trap-and-emulate" process found in full virtualization, leading to higher performance.

**The Xen Architecture in Detail:**

Xen is a classic example of a Type-1 hypervisor that was designed around the concept of paravirtualization.

```ascii
+-----------------------------------------------------------------+
|                           HARDWARE                              |
|      (CPU, Memory, Disk, Network)                               |
+-----------------------+-----------------------------------------+
                        |
+-----------------------+-----------------------------------------+
|                      XEN HYPERVISOR                             |
+-----------------------+-----------------------------------------+
      |                 |                      |
+-----v------+  +-------v--------+       +-----v------+
|   Domain 0 |  |   Domain U 1   |       |   Domain U 2 |
|  (Dom0)    |  |   (DomU)       |       |   (DomU)     |
|------------|  |----------------|       |--------------|
| Privileged |  | Unprivileged   |       | Unprivileged |
|  Guest OS  |  |  Guest OS      |       |  Guest OS    |
| (Linux)    |  | (Linux)        |       | (Windows-HVM)|
|------------|  |----------------|       |--------------|
|  Drivers   |  | Virtual Block  |       | Virtual NIC  |
|  for HW    |  | Device (VBD)   |       | (VIF)        |
+------------+  +----------------+       +--------------+
```

**Components and Functionality:**

1.  **Xen Hypervisor:** This is the core, lightweight layer that runs directly on the hardware. Its main jobs are CPU scheduling and memory partitioning. It has no knowledge of I/O devices like networking or storage.
2.  **Domain 0 (Dom0):** This is a special, privileged virtual machine. It is the first VM to be started and has direct access to the physical hardware. Dom0 runs a modified Linux kernel and contains all the device drivers needed to control the hardware (network cards, disk controllers). It also hosts the control stack tools used to manage the creation and destruction of other VMs. **Dom0 is the management and I/O hub of the Xen system.**
3.  **Domain U (DomU):** These are the unprivileged guest virtual machines. They have no direct access to physical hardware.
    -   **Paravirtualized Guests (PV):** These are modified, "Xen-aware" guest OSes (typically Linux). When a PV guest needs to perform I/O (like reading from a disk), it doesn't try to access the hardware. Instead, it sends a request to Dom0, which then uses its real drivers to perform the I/O on behalf of the guest. This communication is highly efficient.
    -   **Hardware Virtualized Guests (HVM):** Xen can also run unmodified guests (like Windows) by using CPU extensions (Intel VT-x/AMD-V). In this mode, Xen emulates a full PC for the guest.

**Role in Improving Performance:**
Xen's paravirtualized approach improves performance significantly by avoiding the overhead of full emulation. By having the guest OS (DomU) and the management domain (Dom0) cooperate with the hypervisor through hypercalls, I/O and other privileged operations are handled as efficient software calls rather than slow, hardware-level traps. This makes Xen a very lightweight and high-performance virtualization platform.

**(OR)**

**12. (b) Describe the NIST Cloud architecture and explain its characteristics.**

**NIST Cloud Architecture:**

The National Institute of Standards and Technology (NIST) provides a widely accepted definition and framework for cloud computing, which describes its architecture through five essential characteristics, three service models, and four deployment models.

**The Architecture Model:**
The NIST model defines several "actors":
-   **Cloud Consumer:** The person or organization that uses services from a cloud provider.
-   **Cloud Provider:** The organization that makes the cloud services available.
-   **Cloud Auditor:** A third party that conducts independent assessments of security and performance.
-   **Cloud Broker:** An entity that manages the use, performance, and delivery of cloud services and negotiates relationships between providers and consumers.
-   **Cloud Carrier:** The intermediary that provides connectivity and transport of cloud services (e.g., the internet service provider).

**Five Essential Characteristics:**

1.  **On-demand self-service:** A consumer can unilaterally provision computing capabilities, such as server time and network storage, as needed automatically without requiring human interaction with the service provider.
2.  **Broad network access:** Capabilities are available over the network and accessed through standard mechanisms that promote use by heterogeneous thin or thick client platforms (e.g., mobile phones, laptops).
3.  **Resource pooling:** The provider's computing resources are pooled to serve multiple consumers using a multi-tenant model, with different physical and virtual resources dynamically assigned and reassigned according to consumer demand.
4.  **Rapid elasticity:** Capabilities can be elastically provisioned and released, in some cases automatically, to scale rapidly outward and inward commensurate with demand. To the consumer, the capabilities available for provisioning often appear to be unlimited.
5.  **Measured service:** Cloud systems automatically control and optimize resource use by leveraging a metering capability at some level of abstraction appropriate to the type of service (e.g., storage, processing, bandwidth). Resource usage can be monitored, controlled, and reported, providing transparency for both the provider and consumer.

These characteristics are delivered through three **Service Models** (IaaS, PaaS, SaaS) and four **Deployment Models** (Public, Private, Hybrid, Community).

**13. (a) A cloud service provider is planning to expand its infrastructure to offer flexible computing resources to clients. To achieve this, the provider wants to deploy different types of virtual machines (VMs) that can cater to various workload requirements, such as development environments, high-performance computing, and storage optimization. What are the different types of virtual machines that the provider can implement? Discuss each type in detail, including its purpose, characteristics, and suitable use cases.**

A cloud service provider would implement a variety of specialized VM types (often called "instance families") to cater to different customer workloads.

**Types of Virtual Machines by Workload:**

1.  **General Purpose VMs:**
    -   **Purpose:** To provide a balance of CPU, memory, and networking resources.
    -   **Characteristics:** They offer a good ratio of vCPU to RAM (e.g., 1 vCPU to 4 GB RAM) and are suitable for a wide variety of applications.
    -   **Use Cases:** Web servers, small to medium databases, development and testing environments, and enterprise applications like CRMs and ERPs.

2.  **Compute-Optimized VMs:**
    -   **Purpose:** To provide the highest processor performance at the lowest cost per vCPU.
    -   **Characteristics:** They have a high ratio of vCPU to RAM (e.g., 1 vCPU to 2 GB RAM). They often feature the provider's fastest processors.
    -   **Use Cases:** High-performance computing (HPC), scientific modeling, batch processing, video encoding, and CPU-intensive gaming servers.

3.  **Memory-Optimized VMs:**
    -   **Purpose:** To run large in-memory applications.
    -   **Characteristics:** They have a very high ratio of RAM to vCPU (e.g., 1 vCPU to 8 GB RAM or more) and can offer terabytes of memory.
    -   **Use Cases:** In-memory databases (like SAP HANA), real-time big data analytics (like Spark or Presto), and large-scale caching applications.

4.  **Storage-Optimized VMs:**
    -   **Purpose:** Designed for workloads that require very high, low-latency I/O to large datasets on local storage.
    -   **Characteristics:** They come with very fast, local NVMe SSD storage, optimized for millions of I/O operations per second (IOPS).
    -   **Use Cases:** NoSQL databases (like Cassandra, MongoDB), data warehousing, and large transactional databases that require extremely fast disk access.

5.  **Accelerated Computing (GPU) VMs:**
    -   **Purpose:** To provide specialized hardware accelerators, primarily Graphics Processing Units (GPUs).
    -   **Characteristics:** These VMs are equipped with powerful NVIDIA or AMD GPUs.
    -   **Use Cases:** Machine learning model training and inference, artificial intelligence (AI), graphics rendering, and virtual desktop infrastructure (VDI) for graphics-intensive applications like CAD software.

By offering these different types, the cloud provider gives clients the flexibility to choose the most cost-effective and performant VM for their specific application, rather than using a one-size-fits-all approach.

**(OR)**

**13. (b) A mid-sized company is facing challenges with underutilized physical servers, high maintenance costs, and inefficient resource allocation. To optimize infrastructure, the IT team is exploring server virtualization as a solution. What are the different types of server virtualization that the company can implement to address these issues? Explain each type in detail, highlighting how they can help in improving resource utilization and reducing costs.**

To address its challenges, the company can implement two main types of server virtualization.

**1. Traditional VM-Based Virtualization (using a Type-1 Hypervisor):**

-   **Explanation:** This is the most common form of server virtualization. A Type-1 hypervisor (like VMware ESXi or Microsoft Hyper-V) is installed on the physical servers. This allows the company to run multiple, isolated virtual machines (VMs) on each physical host. Each VM runs its own complete guest operating system (e.g., Windows or Linux).
-   **How it Helps:**
    -   **Improves Resource Utilization:** This directly solves the problem of underutilization. Instead of having one application running on a server at 10% capacity, the company can run 10 or more VMs on a single server, driving its utilization up to 70-80%. This is achieved through **server consolidation**.
    -   **Reduces Costs:** By consolidating many physical servers onto a few virtualized hosts, the company drastically reduces hardware maintenance contracts, power consumption, and cooling costs.
    -   **Efficient Resource Allocation:** The hypervisor can dynamically allocate resources to VMs as needed. If one VM is idle, its resources can be used by another, busier VM on the same host.

**2. Operating System-Level Virtualization (Containerization):**

-   **Explanation:** This is a lighter-weight alternative. Instead of virtualizing the hardware, this method virtualizes the operating system. Multiple isolated user-space instances, called **containers**, run on a single shared host OS kernel. Popular platforms include Docker and Kubernetes.
-   **How it Helps:**
    -   **Improves Resource Utilization:** Containers are much more lightweight than VMs because they don't have the overhead of a full guest OS. This means a single host can run many more containers than VMs, leading to even higher density and resource utilization.
    -   **Reduces Costs:** The higher density translates to needing even fewer physical servers, further reducing costs.
    -   **Efficient Resource Allocation:** Containers start in seconds (vs. minutes for VMs), making them extremely efficient for modern, microservices-based applications where resources need to be allocated and de-allocated very quickly.

**Recommendation for the Company:**

The company should likely use a **combination of both**.
-   Use **VM-based virtualization** to migrate their existing, traditional applications (a process known as "lift-and-shift"). This is the most straightforward way to virtualize what they already have.
-   For new, modern applications, they should explore **containerization**, as it offers greater efficiency and agility for cloud-native development practices.
