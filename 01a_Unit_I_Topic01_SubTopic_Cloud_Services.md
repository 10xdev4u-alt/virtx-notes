---
title: "Unit I, Sub-Topic: Cloud Computing Service Models"
id: unit1-topic1a-cloud-services
tags:
  - unit1
  - cloud-computing
  - iaas
  - paas
  - saas
aliases:
  - IaaS, PaaS, SaaS
  - Cloud Service Models
links:
  - "[[01_Unit_I_Topic01_Virtualization_and_Cloud_Computing]]"
  - "[[01b_Unit_I_Topic01_SubTopic_Cloud_Deployment_Models]]"
---

# Sub-Topic: Cloud Computing Service Models

While virtualization is the engine, cloud computing is the service delivered by that engine. These services are typically categorized into three main models: IaaS, PaaS, and SaaS. Understanding these is essential for knowing how virtualized resources are consumed.

> [!quote] **Analogy: The Pizza Service**
> This is a classic analogy to understand the difference.
> - **On-Premises:** You make everything yourself. You buy the ingredients, use your own oven, and serve it at your own table. (You manage everything).
> - **IaaS:** You buy a pre-made pizza base with sauce. You add your own toppings and bake it in your own oven. (You manage the OS, applications, and data).
> - **PaaS:** You order a pizza for delivery. You don't make it, but you provide the table and drinks. (You manage your application and data).
> - **SaaS:** You go out to a pizza restaurant. You just sit down and eat. (You manage nothing).

## 1. IaaS (Infrastructure as a Service)

-   **What it is:** This is the most basic cloud service model. The cloud provider offers fundamental computing infrastructure—virtualized servers (VMs), networking, and storage—over the internet. It is essentially a virtual data center.
-   **What you manage:** You are responsible for managing the operating system (e.g., installing Windows/Linux), installing and managing your applications, and all of your data.
-   **What the provider manages:** The provider manages the underlying physical hardware, the data center, and the virtualization (hypervisor) layer.
-   **Use Case:** Migrating on-premises applications to the cloud ("lift-and-shift"), disaster recovery, and situations where you need maximum control over the OS and environment.
-   **Examples:** Amazon EC2, Google Compute Engine, Microsoft Azure VMs.

## 2. PaaS (Platform as a Service)

-   **What it is:** This model provides a platform that allows customers to develop, run, and manage applications without the complexity of building and maintaining the underlying infrastructure. It abstracts away the OS, servers, and networking.
-   **What you manage:** You are only responsible for your **application code** and your **data**.
-   **What the provider manages:** The provider manages everything else: the hardware, the hypervisor, the operating system, patching, and the runtime environment (e.g., Java, Python, .NET runtimes).
-   **Use Case:** Application development and deployment, where developers want to focus purely on writing code without worrying about the underlying infrastructure.
-   **Examples:** AWS Elastic Beanstalk, Heroku, Google App Engine, Microsoft Azure App Service.

## 3. SaaS (Software as a Service)

-   **What it is:** This is the most common model. It delivers a complete software application over the internet on a subscription basis. The entire application is managed by the provider.
-   **What you manage:** Essentially nothing except your user data within the application.
-   **What the provider manages:** Everything—the application itself, the data, the runtime, the OS, the servers, and all the infrastructure.
-   **Use Case:** End-user applications that you access via a web browser or mobile app.
-   **Examples:** Google Workspace (Gmail, Google Docs), Microsoft Office 365, Salesforce, Dropbox.

## Summary Table: Management Responsibility

| Manages...          | On-Premises | IaaS (Infrastructure) | PaaS (Platform) | SaaS (Software) |
|---------------------|-------------|-----------------------|-----------------|-----------------|
| **Applications**    | **You**     | **You**               | **You**         | Provider        |
| **Data**            | **You**     | **You**               | **You**         | Provider        |
| **Runtime**         | **You**     | **You**               | Provider        | Provider        |
| **Operating System**| **You**     | **You**               | Provider        | Provider        |
| **Virtualization**  | **You**     | Provider              | Provider        | Provider        |
| **Servers**         | **You**     | Provider              | Provider        | Provider        |
| **Storage**         | **You**     | Provider              | Provider        | Provider        |
| **Networking**      | **You**     | Provider              | Provider        | Provider        |

> [!success] **Exam Focus**
> - **10-Mark Question:** "Elaborate on the different types of cloud computing services available."
>   - **Answer Strategy:** Define and explain IaaS, PaaS, and SaaS. For each model, describe what it is, what the user manages vs. what the provider manages, and provide a clear example. Using the Pizza Analogy and the management responsibility table will make your answer comprehensive and easy to understand.
