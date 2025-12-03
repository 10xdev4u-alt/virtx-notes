---
title: "Unit V, Topic 06: Case Study - Choosing a Virtualization Platform"
id: unit5-topic6-case-study
tags:
  - unit5
  - tools
  - case-study
  - platform-selection
aliases:
  - Virtualization Case Study
links:
  - "[[00_Syllabus]]"
  - "[[27_Unit_V_Topic05_IBM_PowerVM]]"
  - "[[ClgMatx/SemVPrep/VirtX/Unit_05_Quiz]]"
---

# Unit V, Topic 06: Case Study - Choosing a Virtualization Platform

This case study synthesizes our knowledge of the various virtualization platforms by applying it to a realistic business scenario. The goal is to analyze a set of requirements and make a justified recommendation.

## The Scenario

A mid-sized manufacturing company with 500 employees needs to refresh its aging data center. They currently have 20 physical servers running a mix of applications. Their IT department consists of 5 people who are experienced Windows Server administrators but have limited experience with Linux and no experience with enterprise storage (SANs).

**Key Requirements & Constraints:**

1.  **Workloads:**
    -   70% of their servers run Windows-based applications (Microsoft SQL Server, SharePoint, Active Directory, File Servers).
    -   30% run Linux for custom in-house applications.
2.  **Budget:** The company is cost-conscious and wants to maximize the return on its investment. They have an existing Microsoft Enterprise Agreement, which provides them with Windows Server Datacenter licenses.
3.  **Staff Skills:** The IT staff is highly proficient with Windows Server and its management tools (like PowerShell) but has minimal Linux command-line expertise.
4.  **Future Strategy:** The CIO has a "cloud-first" mandate for new applications and is looking for a solution that will facilitate a future **hybrid cloud** strategy with Microsoft Azure.
5.  **Features:** They require standard enterprise features like high availability and live migration to reduce downtime during maintenance.

## The Analysis

Let's evaluate the main platform options based on the company's requirements.

### Option 1: VMware vSphere
-   **Pros:**
    -   Market leader with a very mature, feature-rich platform.
    -   Excellent performance and a vast ecosystem of support.
-   **Cons:**
    -   **High Cost:** Would require a significant new investment in vSphere and vCenter licensing, which is not covered by their existing Microsoft agreement.
    -   **Learning Curve:** The IT staff would need to be trained on a completely new platform (ESXi, vCenter), which adds time and cost to the project.
    -   While it has hybrid cloud capabilities, the integration might not be as seamless with Azure as a native Microsoft solution.

### Option 2: KVM (or an open-source platform like Proxmox)
-   **Pros:**
    -   **No Licensing Cost:** The hypervisor itself is free and open-source.
-   **Cons:**
    -   **Major Skills Gap:** The Windows-centric IT staff has limited Linux expertise, which would be a significant barrier to deploying, managing, and troubleshooting a KVM-based environment effectively.
    -   **Support Costs:** While the software is free, they would likely need to pay for a commercial support contract, which can be expensive.
    -   **Management Complexity:** Often requires more command-line work or third-party tools to achieve the same level of management simplicity as vSphere or Hyper-V.

### Option 3: Microsoft Hyper-V
-   **Pros:**
    -   **Cost-Effective:** The Hyper-V role is included in their existing Windows Server Datacenter licenses. This is a massive financial advantage.
    -   **Leverages Existing Skills:** The IT staff can use their existing Windows Server and PowerShell knowledge to manage the platform. Tools like Hyper-V Manager and System Center are familiar.
    -   **Seamless Hybrid Cloud Integration:** As a Microsoft product, it is designed for deep integration with Azure. Features like Azure Arc and Azure Stack HCI provide a direct and smooth path for their hybrid cloud strategy.
    -   **Feature Parity:** Provides the required enterprise features like Live Migration and Failover Clustering.
    -   **Good Linux Support:** Modern versions of Hyper-V have excellent support for running Linux guest VMs.

-   **Cons:**
    -   Ecosystem is not as vast as VMware's, but is more than sufficient for this company's needs.

## The Recommendation and Justification

**Recommendation:** **Microsoft Hyper-V**

**Justification:**

Microsoft Hyper-V is the clear and logical choice for this organization. The recommendation is based on a holistic view of the company's specific business and technical requirements:

1.  **Financial Alignment:** The solution leverages their existing Microsoft Enterprise Agreement, making the hypervisor platform essentially free and dramatically lowering the project's Total Cost of Ownership (TCO).
2.  **Operational Alignment:** It aligns perfectly with the existing skillset of the IT staff. This reduces training costs, minimizes implementation risk, and ensures the team can manage the new environment effectively from day one.
3.  **Strategic Alignment:** It provides the most direct and seamless path to fulfilling the CIO's hybrid cloud mandate with Microsoft Azure.
4.  **Technical Sufficiency:** It meets all stated technical requirements, including support for both Windows and Linux workloads and providing essential enterprise features like high availability and live migration.

While VMware vSphere is an excellent platform, its higher cost and the required staff retraining make it a less optimal choice for this specific scenario. KVM is not a good fit due to the significant skills gap of the IT team. Therefore, Hyper-V provides the best balance of cost, features, and strategic alignment for this company.

> [!success] **Exam Focus**
> You will almost certainly get a case study question on your final exam.
> - **How to Answer:** Do not just state a recommendation. You must **justify** it.
> - **Structure your answer:**
>   1.  **Analyze:** Briefly list the key requirements from the scenario (e.g., Budget, Skills, Strategy).
>   2.  **Evaluate:** Briefly discuss the pros and cons of at least two alternative platforms (e.g., "VMware would be too expensive because...").
>   3.  **Recommend:** Clearly state your recommended platform.
>   4.  **Justify:** Provide a detailed justification, linking your recommendation directly back to the specific requirements you identified in the analysis step. This shows the examiner that you made a logical, evidence-based decision.
