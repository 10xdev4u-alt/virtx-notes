---
title: "Unit V, Topic 03: Cloud Platforms (AWS and Google)"
id: unit5-topic3-cloud-platforms
tags:
  - unit5
  - tools
  - cloud
  - aws
  - gcp
  - ec2
  - iaas
aliases:
  - AWS Virtualization
  - Google Cloud Virtualization
links:
  - "[[00_Syllabus]]"
  - "[[24_Unit_V_Topic02_Microsoft_Hyper-V]]"
  - "[[26_Unit_V_Topic04_Oracle_VM_VirtualBox]]"
---

# Unit V, Topic 03: Cloud Platforms (AWS and Google)

While VMware and Microsoft provide the tools for organizations to build their own private clouds, public cloud providers like Amazon Web Services (AWS) and Google Cloud Platform (GCP) are massive consumers of virtualization technology, which they package and sell as a service. They represent a different way of consuming virtualized resources.

## 5.3.1 Amazon Web Services (AWS)

AWS is the world's leading public cloud platform. Virtualization is the bedrock upon which its entire Infrastructure as a Service (IaaS) offering is built.

### Core Virtualization Service: Amazon EC2
-   **What it is:** **Amazon Elastic Compute Cloud (EC2)** is the service that provides resizable compute capacity—virtual servers—in the cloud. When you "launch an EC2 instance," you are provisioning a virtual machine on Amazon's massive infrastructure.
-   **Underlying Technology:** AWS uses a highly customized version of the **Xen** and **KVM** Type-1 hypervisors. They developed their own lightweight hypervisor based on KVM, called the **Nitro System**, which offloads networking and storage functions to dedicated hardware, maximizing performance for the guest instances.
-   **Key Characteristics:**
    -   **Elasticity:** Users can launch or terminate instances in minutes.
    -   **Variety:** Offers hundreds of instance types optimized for different workloads (e.g., general purpose, compute-optimized, memory-optimized).
    -   **Pay-as-you-go:** Users pay only for the resources they consume.

### Other Virtualized Services in AWS
-   **Network Virtualization:** **Amazon VPC (Virtual Private Cloud)** allows users to provision a logically isolated section of the AWS Cloud where they can launch resources in a virtual network that they define.
-   **Storage Virtualization:**
    -   **Amazon EBS (Elastic Block Store):** Provides block-level storage volumes (virtual disks) for use with EC2 instances.
    -   **Amazon S3 (Simple Storage Service):** Provides highly scalable object storage.

## 5.3.2 Google Cloud Platform (GCP)

Google Cloud Platform (GCP) is another major public cloud provider that leverages its vast global infrastructure and expertise in open-source technologies.

### Core Virtualization Service: Google Compute Engine
-   **What it is:** **Google Compute Engine (GCE)** is GCP's IaaS offering that allows users to create and run virtual machines on Google's infrastructure.
-   **Underlying Technology:** Google is a heavy proponent of open-source technology. GCE virtual machines run on a distributed system that uses a highly customized version of the **KVM** Type-1 hypervisor. Google has contributed significantly to KVM's development.
-   **Key Characteristics:**
    -   **Live Migration:** GCP was a pioneer in offering transparent live migration for customer VMs during host maintenance, a feature that was traditionally complex in on-premises environments.
    -   **Custom Machine Types:** Offers high flexibility in configuring the exact amount of vCPU and memory for a VM.

### Other Virtualized Services in GCP
-   **Network Virtualization:** **Google Virtual Private Cloud (VPC)** provides global, software-defined networking for GCP resources.
-   **Storage Virtualization:** **Persistent Disk** provides block storage for GCE instances, while **Cloud Storage** provides object storage.

## Key Takeaway: Virtualization as a Service

The fundamental difference between using VMware/Hyper-V and using AWS/GCP is the level of abstraction.

-   With **on-premises virtualization (VMware/Hyper-V)**, you manage the entire stack, from the physical hardware and hypervisor up to the guest VM. You are the **operator** of the virtualization platform.
-   With **public cloud virtualization (AWS/GCP)**, the physical hardware and the hypervisor layer are completely abstracted away. You only manage the guest VM (the "instance") and the virtualized network and storage. You are a **consumer** of virtualization as a service.

> [!success] **Exam Focus**
> - **4-Mark Question:** "Explain the role of virtualization in a public cloud platform like AWS."
>   - **Answer Strategy:** Explain that virtualization is the core enabling technology. State that services like **Amazon EC2** use hypervisors (like KVM/Xen) to provide virtual machines (instances) to customers on demand. Mention that other services like **VPC** (network virtualization) and **EBS** (storage virtualization) are also built on these principles, allowing AWS to offer a complete, virtualized data center as a service.
> - **2-Mark Question:** "What hypervisor does Google Compute Engine primarily use?"
>   - **Answer:** Google Compute Engine primarily uses a customized version of the open-source **KVM** (Kernel-based Virtual Machine) hypervisor.
