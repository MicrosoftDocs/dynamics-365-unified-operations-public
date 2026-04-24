---
title: Plan and prepare for on-premises deployments
description: Learn how you can plan and prepare for your on-premises deployment, including an overview of difference between cloud and on-premises deployments.
author: faix
ms.author: osfaixat
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 04/02/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2017-12-20
ms.dyn365.ops.version: Platform Update 8
ms.service: dynamics-365-op
---

# Plan and prepare for on-premises deployments

[!include [banner](../includes/banner.md)]

Dynamics 365 Finance + Operations (on-premises) supports running business processes in customer data centers. With this deployment option, application servers and the Microsoft SQL Server database run in the customer’s data center.

This article helps you plan and prepare for your on-premises deployment.

> [!IMPORTANT]
> Dynamics 365 Finance + Operations (on-premises) isn't supported on any public cloud infrastructure, including Microsoft Azure Cloud services. However, it's supported to run on [Microsoft Azure Stack HCI](https://azure.microsoft.com/products/azure-stack/hci/) and [Microsoft Azure Stack Hub](https://azure.microsoft.com/products/azure-stack/hub/).

## Differences between cloud deployments and on-premises deployments

The features in cloud deployments and on-premises deployments differ. These differences affect your planning. The differences are described in the following topics:

- [Deployment options](choose-deployment-type.md)
- [Comparison of cloud and on-premises features](../../fin-ops/get-started/cloud-prem-comparison.md)
- [Removed or deprecated features for finance and operations](../migration-upgrade/deprecated-features.md)

## How to use Lifecycle Services with on-premises deployments

Microsoft Dynamics Lifecycle Services is an application management portal that provides tools and services for managing the application lifecycle. Customers and partners use Lifecycle Services to manage both cloud and on-premises deployments. Use Lifecycle Services for the following tasks:

- Deploy cloud and on-premises environments.
- Service your environments.
- Monitor, diagnose, and analyze the health of the environments that you manage (cloud only).
- Search for product issues and regulatory features.
- Obtain support.

For more information about Lifecycle Services, see [Lifecycle Services resources](../lifecycle-services/lcs.md).

## Environments

Plan for four types of environments. This section describes the four environments and how to access and deploy them.

### Demo environment

Sign up for a demo environment to learn about the system. The demo environment is applicable to both cloud and on-premises deployments. For more information, see [Sign up for preview subscriptions](../dev-tools/sign-up-preview-subscription.md).

### Developer environment

The development experience is the same for cloud and on-premises deployments. To access a developer environment, see [Deploy and access development environments](../dev-tools/access-instances.md).

### Sandbox environment

Business users and functional team members validate application functionality by using a sandbox environment. This functionality includes customizations and data that you bring forward from Microsoft Dynamics AX 2012 environments. To deploy an on-premises sandbox environment, see [Set up and deploy on-premises environments home page](setup-deploy-on-premises-environments.md).

At a minimum, an on-premises sandbox environment requires:

- Three machines running Environment Orchestrator
- Two machines running Application Object Servers (AOS)
- One machine running SQL Server Integration Services (SSIS)
- One machine running Management Reporter (MR)
- One machine running SQL Server Reporting Services (SSRS) with a local SQL Server (Database Engine)
- One machine running Active Directory
- One machine running SQL Server (Database Engine)

### Production environment

The production environment is the live deployment that your users and customers access. To deploy a production environment, see [Set up and deploy on-premises environments home page](setup-deploy-on-premises-environments.md).

At a minimum, an on-premises production environment requires:

- Three machines running Environment Orchestrator
- Three machines running Application Object Servers (AOS)
- One machine running SQL Server Integration Services (SSIS)
- One machine running Management Reporter (MR)
- One machine running SQL Server Reporting Services (SSRS) with a local SQL Server (Database Engine)
- Two or more machines running SQL Server (Database Engine). Failover is only supported in an active\passive configuration.
- Two or more machines running Active Directory

## Service Fabric

An on-premises deployment uses Azure Service Fabric standalone clusters. Service Fabric is the next generation Microsoft middleware platform for building and managing enterprise-class, high-scale applications. You can deploy Service Fabric standalone clusters on any computer that runs Windows Server.

An on-premises deployment has a standalone cluster for each sandbox environment and a standalone cluster for each production environment. You deploy the following roles or node types into both types of clusters:

- Application Object Servers (AOS) – Provides the ability to run the application functionality in client, batch, and import/export scenarios.
- Management Reporter (MR) – Provides financial reporting functionality.
- SQL Server Reporting Services (SSRS) – Provides document reporting functionality.
- Environment Orchestrator – Enables on-premises environment management from Lifecycle Services.

The following diagram shows the node types deployed in a Service Fabric standalone cluster.

:::image type="content" source="media/on-premises-overview-01.png" alt-text="Screenshot of node types deployed in a Service Fabric standalone cluster.":::

### Service Fabric resources

To learn more about Service Fabric, see the following topics:

- [Azure Service Fabric](/azure/service-fabric).
- [Service Fabric application upgrade](/azure/service-fabric/service-fabric-application-upgrade) - An Azure Service Fabric application is a collection of services that requires periodic upgrades.
- [Plan and prepare your Service Fabric standalone cluster deployment](/azure/service-fabric/service-fabric-cluster-standalone-deployment-preparation) - Additional information about Service Fabric clusters and antivirus exclusions.

## System requirements

Review the system requirements in [System requirements for on-premises deployments](../../fin-ops/get-started/system-requirements-on-prem.md) and be aware of the number of machines that are required for on-premises deployments.

## Hardware sizing

Before you begin the hardware and infrastructure sizing process for an on-premises environment, review the [System requirements for on-premises deployments](../../fin-ops/get-started/system-requirements-on-prem.md) and the [Set up and deploy on-premises environments home page](setup-deploy-on-premises-environments.md) to gain a solid understanding of the underlying infrastructure. Pay close attention to the system setup best practices for optimum performance. After you review the documentation, start the process of estimating your transactional and concurrent user volume and sizing your environment based on the average core throughput.

### Factors that affect sizing

The core factors that affect sizing are:

- Transaction characterization
- User characterization - Type and concurrency
- Data composition
- Extensions
- Reporting usage patterns
- Third-party solutions

The more detailed data you collect, the more precisely you can estimate sizing. Hardware sizing without supporting data is likely to be inaccurate. Collect at least the peak transaction line load per hour. The following diagram shows the factors that affect sizing.

:::image type="content" source="media/sizing-factors.png" alt-text="Screenshot of sizing factors diagram.":::

From left to right, the first and most important factor needed to accurately estimate sizing is a transaction profile or a transaction characterization. Find the peak transactional volume per hour. If multiple peak periods exist, accurately define these periods.

As you understand the load that impacts your infrastructure, also understand more detail about these factors:

- **Transactions** – Transactions typically have certain peaks throughout the day or week. The peaks might depend on the transaction type. For example, time and expense entries usually show peaks once per week, while sales orders might arrive in bulk via integration or trickle in during the day.
- **Number of concurrent users** – The number of concurrent users is the second most important sizing factor. You can't get reliable sizing estimates based only on the number of concurrent users. If concurrent users are the only data that you have available, estimate an approximate number for transactions, and revisit this estimate when you have more data. An accurate concurrent user definition means that:
  - Named users aren't concurrent users.
  - Concurrent users are always a subset of named users.
  - Peak workload defines the maximum concurrency for sizing.
    For concurrent users, the user must meet all the following criteria:
    - The user is logged on.
    - There are working transactions or inquiries at the time of counting.
    - The session isn't idle.
- **Data composition** – Data composition is how your system is set up and configured. For example, this setup can include the number of legal entities, the number of items, the number of BOM levels, and how complex the security setup is. Each of these factors might have an impact on performance. However, smart choices for infrastructure can offset the impact.
- **Extensions** – Customizations can be simple or complex. The number of customizations and the nature of complexity and usage have a varied impact on the size of the infrastructure needed. For complex customizations, conduct performance evaluations to ensure that they aren't only tested for efficiency but also help understand the infrastructure needs. This consideration is even more critical when the extensions aren't coded according to best practices for performance and scalability.
- **Reporting and analytics** – Reporting and analytics typically include running heavy queries against the database systems. Reducing the frequency of when data intensive reports run helps reduce their impact. It’s also important to understand how the design of your queries impacts their performance.
- **Third-party solutions** – These solutions, like ISVs, have the same implications and recommendations as extensions.

## Sizing your environment

To determine your sizing requirements, first identify the peak volume of transactions that you need to process. Most auxiliary systems, like Management Reporter or SSRS, are less mission critical. As a result, this article focuses primarily on AOS and SQL Server.

In general, scale out the compute tiers and set them up in an N+1 fashion. For example, if you estimate three AOS, add a fourth AOS. Set up the database tier in an Always On highly available configuration.

### SQL Server (OLTP)

#### Sizing

- 3,000 to 15,000 transaction lines per hour per core on the database server.
- Typical AOS-to-SQL core ratio is 3:1 for the primary SQL Server. High-availability configurations require extra cores.
  - Processing database-heavy operations can change this ratio to 2:1.
- The following factors can cause variations in performance:
  - Parameter settings.
  - Levels of extensions.
  - Usage of extra functionality, such as database logs and alerts. Extreme database logging reduces throughput per hour per core to less than 3,000 lines.
  - Complexity of data composition. For example, a simple chart of accounts versus a detailed fine-grained chart of accounts affects throughput.
  - Transaction characterization.
  - 2 GB to 4 GB memory for each core.
  - Auxiliary databases on the database server, such as Management Reporter and SSRS databases.
  - Temp DB = 15% of DB size, with as many files as physical processors.
  - SAN size and throughput based on total concurrent transaction volume and usage.

#### High availability

Always use SQL Server in either a cluster or mirroring setup. The second SQL node should have the same number of cores as the primary node. Failover is only supported in an active\passive configuration.

#### Active Directory Federation Services (AD FS)

For AD FS sizing, see the [AD FS Server Capacity documentation](/windows-server/identity/ad-fs/design/planning-for-ad-fs-server-capacity). A [sizing spreadsheet](https://adfsdocs.blob.core.windows.net/adfs/ADFSCapacity2016.xlsx) is available for planning the number of instances in your deployment.

### AOS (Online and batch)

#### Sizing

- Size by transaction volume and usage:
  - 2,000 to 6,000 lines per core
  - 16 GB per instance
  - Standard box – 4 to 24 cores
  - 10 to 15 Enterprise users per core
  - 15 to 25 Activity users per core
  - 25 to 50 Team members per core
- Batch
  - 1 to 4 batch threads per core
  - Size based on batch window characterization
- In Service Fabric, AOS, Data Management, and Batch are the same role. You need to size for these three workloads combined, and not separately as you did with Microsoft Dynamics AX 2012.
- The same variability factors for SQL Server apply here.

#### High availability

- Ensure that you have at least one to two more AOS available than you estimate.
- Ensure that you have at least three to four virtual hosts available.

### SQL integration services (SSIS)

The recommended minimum requirements of two nodes should suffice for most integration uses. In scenarios involving high levels of integrations, you might need more than two nodes. When this happens, scale up accordingly.

### Management reporter

In most cases, unless used extensively, the recommended minimum requirements using two nodes work well. Only in cases of heavy use do you need more than two nodes. Then, scale as needed.

### SQL Server Reporting Services

For the current release of Finance + Operations, you can deploy only one SSRS node. Monitor your SSRS node while testing and increase the number of cores available for SSRS as needed. Make sure that you have a preconfigured secondary node available on a virtual host that is different from the SSRS VM. This configuration is important if there's an issue with the virtual machine that hosts SSRS or the virtual host. If this problem occurs, you need to replace the node.

### Environment Orchestrator

The Orchestrator service manages your deployment and the related communication with Lifecycle Services. This service is the primary Service Fabric service and requires at least three VMs. This service colocates with the Service Fabric orchestration services. Size this service to the peak load of the cluster. For more information, see [Plan and prepare your Service Fabric Standalone cluster deployment](/azure/service-fabric/service-fabric-cluster-standalone-deployment-preparation).

### Virtualization and oversubscription

Host mission critical services like the AOS on virtual hosts that have dedicated resources such as core, memory, and disk.

## Authentication methods

Use the following authentication methods with on-premises deployments:

- **Microsoft Entra ID** - Use Microsoft Entra ID as the authentication method to sign in to Lifecycle Services. Use Microsoft Entra to configure the Lifecycle Services Local Agent. For more information, see [What is Microsoft Entra ID?](/azure/active-directory/active-directory-whatis)
- **Active Directory Domain Services (AD DS)** - The machines that host Finance + Operations components must belong to an Active Directory domain. You must configure Active Directory Domain Services (AD DS) in native mode. For more information, see [Active Directory Domain Services](/windows-server/identity/ad-ds/active-directory-domain-services).
- **Active Directory Federation Services (AD FS)** - Use AD FS as the authentication method in an on-premises deployment. AD FS provides access control and single sign-on across a wide variety of applications including Microsoft 365, cloud-based SaaS applications, and applications on the corporate network.
  - For the IT organization, it enables you to provide sign-on and access control to both modern and legacy applications, on-premises and in the cloud, based on the same set of credentials and policies.
  - For the user, it provides seamless sign-on using the same, familiar account credentials.
  - For the developer, it provides an easy way to authenticate users whose identities live in the organizational directory. This means you can focus your efforts on your application, not authentication, or identity.

    For more information, see [Active Directory Federation Services](/windows-server/identity/active-directory-federation-services).

## Data stored in Azure data centers

The on-premises deployment option for Finance + Operations stores core customer data on-premises. Core customer data is a subset of the customer data definition provided in the [Microsoft Trust Center](https://www.microsoft.com/trustcenter/privacy/how-microsoft-defines-customer-data).

The following table outlines the services that store customer data in Azure data centers located in the United States. The services include Lifecycle Services, Microsoft Office sign up portal, and Microsoft Entra ID. These services enable initial onboarding, initiation, tracking of support incidents, and service updates and upgrades. All other customer data, referred to as core customer data, is stored on-premises.

| Supporting services               | Customer data definition                      |
|---------------------------------------|----------------------------------------------------|
| Microsoft Dynamics Lifecycle Services | Project content and files are stored in a project. This content includes application configuration data, code, metadata, and data assets that include the application and business process models. |
| Microsoft Office signup portal        | Customer information that is collected during the onboarding process.  |
| Microsoft Entra ID      | Authentication for Lifecycle Services and Azure DevOps.   |

You can configure additional services or components to extend an on-premises deployment. However, some configuration choices might transfer core customer data outside of the customer’s data center. For example, configuring data management features that integrate external services with an on-premises deployment might result in the transfer of core customer data outside the on-premises deployment.

## Next steps

After you complete the planning activities mentioned in this article, you can begin the procedures listed in the [Onboard](on-premises-deployment-landing-page.md#onboard) section of the [On-premises deployment home page](on-premises-deployment-landing-page.md).

Refer to the [On-premises deployment home page](on-premises-deployment-landing-page.md) throughout your implementation for more information about planning, deployment, maintenance, and troubleshooting.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
