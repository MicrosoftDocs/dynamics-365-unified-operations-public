---
title: Plan and prepare for on-premises deployments
description: This article will help you plan and prepare for your on-premises deployment.
author: faix
ms.date: 01/26/2022
ms.topic: article
ms.prod: dynamics-365
ms.technology: 
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: osfaixat
ms.search.validFrom: 2017-12-20
ms.dyn365.ops.version: Platform Update 8
ms.custom: 60373
ms.assetid: 
ms.service: 
search.app:
  - financeandoperationsonprem-docs
---

# Plan and prepare for on-premises deployments

[!include [banner](../includes/banner.md)]

Dynamics 365 Finance + Operations (on-premises) supports running business processes in customer data centers. With this deployment option, application servers and the Microsoft SQL Server database will run in the customer’s data center.

This article will help you plan and prepare for your on-premises deployment.

> [!IMPORTANT]
> Dynamics 365 Finance + Operations (on-premises) is not supported on any public cloud infrastructure, including Microsoft Azure Cloud services. However, it is supported to run on [Microsoft Azure Stack HCI](https://azure.microsoft.com/products/azure-stack/hci/) and [Microsoft Azure Stack Hub](https://azure.microsoft.com/products/azure-stack/hub/).

## Differences between cloud deployments and on-premises deployments
The features in cloud deployments and on-premises deployments differ. These differences will affect your planning. The differences are described in the following topics:
- [Deployment options](choose-deployment-type.md)
- [Comparison of cloud and on-premises features](../../fin-ops/get-started/cloud-prem-comparison.md)
- [Removed or deprecated features for finance and operations](../migration-upgrade/deprecated-features.md)

## How LCS is used with on-premises deployments
Microsoft Dynamics Lifecycle Services (LCS) is an application management portal that provides tools and services for managing the application lifecycle. Customers and partners use LCS to manage both cloud and on-premises deployments. You can use LCS for the following tasks:
- Deploy cloud and on-premises environments.
- Service your environments.
- Monitor, diagnose, and analyze the health of the environments that you manage (cloud only).
- Search for product issues and regulatory features.
- Obtain support.

For more information about LCS, see [Lifecycle Services resources](../lifecycle-services/lcs.md).

## Environments
There are four types of environments that you need to plan for. This section describes the four environments and how to access and deploy them.

### Demo environment
You can sign up for a demo environment to learn about the system. The demo environment is applicable to both cloud and on-premises deployments. For more information, see [Sign up for preview subscriptions](../dev-tools/sign-up-preview-subscription.md).

### Developer environment
The development experience is the same for cloud and on-premises deployments. To access a developer environment, see [Deploy and access development environments](../dev-tools/access-instances.md).

### Sandbox environment
Business users and functional team members validate application functionality by using a sandbox environment. This functionality includes customizations and data that was brought forward from Microsoft Dynamics AX 2012 environments. To deploy an on-premises sandbox environment, see [Set up and deploy on-premises environments home page](setup-deploy-on-premises-environments.md).

At a minimum, an on-premises sandbox environment requires:
- 3 machines running Environment Orchestrator
- 2 machines running Application Object Servers (AOS)
- 1 machine running Management Reporter (MR)
- 1 machine running SQL Server Reporting Services (SSRS) with a local SQL Server (Database Engine)
- 1 machine running Active Directory
- 1 machine running SQL Server (Database Engine)

### Production environment
The production environment is the live deployment that your users and customers have access to. To deploy a production environment, see [Set up and deploy on-premises environments home page](setup-deploy-on-premises-environments.md).

At a minimum, an on-premises production environment requires:
- 3 machines running Environment Orchestrator
- 3 machines running Application Object Servers (AOS)
- 1 machine running Management Reporter (MR)
- 1 machine running SQL Server Reporting Services (SSRS) with a local SQL Server (Database Engine)
- 2 or more machines running SQL Server (Database Engine)
- 2 or more machines running Active Directory

## Service Fabric
An on-premises deployment uses Azure Service Fabric standalone clusters. Service Fabric is the next-generation Microsoft middleware platform for building and managing enterprise-class, high-scale applications. Service Fabric standalone clusters can be deployed on any computer that is running Windows Server.

An on-premises deployment has a standalone cluster for each sandbox environment and a standalone cluster for each production environment. The following roles or node types are deployed into both types of clusters:
- Application Object Servers (AOS) – Provides the ability to run the application functionality in client, batch, and import/export scenarios.
- Management Reporter (MR) – Provides financial reporting functionality.
- SQL Server Reporting Services (SSRS) – Provides document reporting functionality.
- Environment Orchestrator – Enables on-premises environment management from LCS.

The following diagram shows the node types deployed in a Service Fabric standalone cluster.

![Node types deployed in a Service Fabric standalone cluster.](media/on-premises-overview-01.png)

### Service Fabric resources
To learn more about Service Fabric, see the following topics:
- [Azure Service Fabric documentation](/azure/service-fabric) - To learn more about Service Fabric.
- [Service Fabric application upgrade](/azure/service-fabric/service-fabric-application-upgrade) - An Azure Service Fabric application is a collection of services that requires periodic upgrades.
- [Plan and prepare your Service Fabric standalone cluster deployment](/azure/service-fabric/service-fabric-cluster-standalone-deployment-preparation) - Additional information about Service Fabric clusters and antivirus exclusions.

## System requirements
Review the system requirements in [System requirements for on-premises deployments](../../fin-ops/get-started/system-requirements-on-prem.md) and be aware of the number of machines that are required for on-premises deployments.

## Hardware sizing
Before you begin the hardware and infrastructure sizing process for an on-premises environment, familiarize yourself with the [System requirements for on-premises deployments](../../fin-ops/get-started/system-requirements-on-prem.md) and [Set up and deploy on-premises environments home page](setup-deploy-on-premises-environments.md) to gain a solid understanding of the underlying infrastructure. Pay close attention to the system setup best practices for optimum performance. After you have reviewed the documentation, you can start the process of estimating your transactional and concurrent user volume and sizing your environment based on the average core throughput.

### Factors that affect sizing
The core factors that affect sizing are:
- Transaction characterization
- User characterization - Type and concurrency
- Data composition
- Extensions
- Reporting usage patterns
- Third-party solutions

The more detailed data that you collect, the more precisely you can estimate sizing. Hardware sizing, without supporting data, is likely to be inaccurate. The minimum data that you need to collect is the peak transaction line load per hour. The factors that affect sizing are shown in the following diagram.

![Sizing factors.](media/sizing-factors.png)

From left to right, the first and most important factor needed to accurately estimate sizing is a transaction profile or a transaction characterization. It’s important to find the peak transactional volume per hour. If there are multiple peak periods, then these periods need to be accurately defined.

As you understand the load that impacts your infrastructure, you also need to understand more detail about these factors:
- **Transactions** – Transactions typically have certain peaks throughout the day or week. The peaks might depend on the transaction type. For example, time and expense entries usually show peaks once per week, while sales orders might arrive in bulk via integration or trickle in during the day.
- **Number of concurrent users** – The number of concurrent users is the second most important sizing factor. You cannot get reliable sizing estimates based only on the number of concurrent users. If concurrent users is the only data that you have available, then estimate an approximate number for transactions, and revisit this when you have more data. An accurate concurrent user definition means that:
    - Named users are not concurrent users.
    - Concurrent users are always a subset of named users.
    - Peak workload defines the maximum concurrency for sizing.
    For concurrent users, the user must meet all the following criteria:
        - The user is logged on.
        - There are working transactions or inquiries at the time of counting.
        - The session is not idle.
- **Data composition** – Data composition is how your system will be set up and configured. For example, this can include the number of legal entities, the number items, the number of BOM levels, and how complex the security setup will be. Each of these factors might have an impact on performance, however the impact can be offset by using smart choices when it comes to infrastructure.
- **Extensions** – Customizations can be simple or complex. The number of customizations and the nature of complexity and usage has a varied impact on the size of the infrastructure needed. For complex customizations, you should conduct performance evaluations to ensure that they are not only tested for efficiency but also help understand the infrastructure needs. This is even more critical when the extensions are not coded according to best practices for performance and scalability.
- **Reporting and analytics** – Reporting and analytics typically include running heavy queries against the database systems. Reducing the frequency of when data intensive reports run will help reduce their impact. It’s also important to understand how the design of your queries impacts their performance.
- **Third-party solutions** – These solutions, like ISVs, have the same implications and recommendations as extensions.

## Sizing your environment
To determine your sizing requirements, you must know the peak volume of transactions that you need to process. Most auxiliary systems, like Management Reporter or SSRS, are less mission critical. As a result, this article focuses primarily on AOS and SQL Server.

In general, the compute tiers scale out and should be set up in an N+1 fashion, meaning if you estimate three AOS, add a fourth AOS. The database tier should be set up in an Always On highly-available setup.

### SQL Server (OLTP)

#### Sizing

- 3K to 15K transaction lines per hour per core on DB server.
- Typical AOS-to-SQL core ratio 3:1 for the primary SQL Server. Additional cores are required based on the high-availability configuration.
    - Processing database-heavy operations may regress this to 2:1.
- The following factors influence variations:
    - Parameter settings in use.
    - Levels of extensions.
    - Additional functionality usage, such as database logs and alerts. Extreme database logging will further reduce throughput per hour per core below 3K lines.
    - Complexity of data composition. For example, a simple chart of accounts versus a detailed fine-grained chart of accounts has implications on throughput.
    - Transaction characterization.
    - 2 GB to 4 GB memory for each core.
    - Auxiliary databases on DB server such as Management reporter and SSRS databases.
    - Temp DB = 15% of DB size, with as many files as physical processors.
    - SAN size and throughput based on total concurrent transaction volume/usage.

#### High availability

You should always utilize SQL Server in either a cluster or mirroring setup. The second SQL node should have the same number of cores as the primary node.

#### Active Directory Federation Services (AD FS)
For AD FS sizing, see the [AD FS Server Capacity documentation](/windows-server/identity/ad-fs/design/planning-for-ad-fs-server-capacity). A [sizing spreadsheet](https://adfsdocs.blob.core.windows.net/adfs/ADFSCapacity2016.xlsx) is available for planning the number of instances in your deployment.

### AOS (Online and batch)

#### Sizing

- Sizing by transaction volume/usage
    - 2K to 6K lines per core
    - 16 GB per instance
    - Standard box – 4 to 24 cores
    - 10 to 15 Enterprise users per core
    - 15 to 25 Activity users per core
    - 25 to 50 Team members per core
- Batch
    - 1 to 4 batch threads per core
    - Size based on batch window characterization
- Note that AOS, Data Management, and Batch are the same role in the Service Fabric. You need to size for these three workloads combined, and not separately as you did with Microsoft Dynamics AX 2012.
- The same variability factors for SQL Server apply here.

#### High availability
- Ensure that you have at least 1 to 2 more AOS available than you estimate.
- Ensure that you have at least 3 to 4 virtual hosts available.

### Management reporter
In most cases, unless used extensively, the recommended minimum requirements using two nodes should work well. Only in cases where there is heavy use will you need more than two nodes, after which you can scale as needed.

### SQL Server Reporting Services
For the current release of Finance + Operations, only one SSRS node can be deployed. Monitor your SSRS node while testing and increase the number of cores available for SSRS as needed. Make sure that you have a preconfigured secondary node available on a virtual host that is different than the SSRS VM. This is important if there is an issue with the virtual machine that hosts SSRS or the virtual host. If this the case, the node would need to be replaced.

### Environment Orchestrator
The Orchestrator service is the service that manages your deployment and the related communication with LCS. This service is deployed as the primary Service Fabric service and requires at least three VMs. This service is co-located with the Service Fabric orchestration services. This should be sized to the peak load of the cluster. For more information, see [Plan and prepare your Service Fabric Standalone cluster deployment](/azure/service-fabric/service-fabric-cluster-standalone-deployment-preparation).

### Virtualization and oversubscription
Mission critical services like the AOS should be hosted on Virtual hosts that have dedicated resources – core, memory, and disk.

## Authentication methods

The following authentication methods are used with on-premises deployments:

- **Azure Active Directory (Azure AD)** - Azure AD is the authentication method used to log in to LCS. Azure AD is used configure the LCS Local Agent. For more information, see [What is Azure Active Directory?](/azure/active-directory/active-directory-whatis)
- **Active Directory Domain Services (AD DS)** - The machines that host Finance + Operations components must belong to an Active Directory domain. You must configure Active Directory Domain Services (AD DS) in native mode. For more information, see [Active Directory Domain Services](/windows-server/identity/ad-ds/active-directory-domain-services).
- **Active Directory Federation Services (AD FS)** - AD FS is the authentication method used in an on-premises deployment. AD FS provides access control and single sign on across a wide variety of applications including Microsoft 365, cloud-based SaaS applications, and applications on the corporate network.
  - For the IT organization, it enables you to provide sign on and access control to both modern and legacy applications, on-premises and in the cloud, based on the same set of credentials and policies.
  - For the user, it provides seamless sign on using the same, familiar account credentials.
  - For the developer, it provides an easy way to authenticate users whose identities live in the organizational directory. This means you can focus your efforts on your application, not authentication or identity.

    For more information, see [Active Directory Federation Services](/windows-server/identity/active-directory-federation-services).

## Data stored in Azure data centers

The on-premises deployment option for Finance + Operations stores core customer data on-premises. Core customer data is a subset of the customer data definition provided in the [Microsoft Trust Center](https://www.microsoft.com/trustcenter/privacy/how-microsoft-defines-customer-data).

The following table outlines the services that are used to store customer data in Azure data centers located in the United States. Services include Lifecycle Services (LCS), Microsoft Office signup portal, and Azure Active Directory. These services enable initial onboarding, initiation, tracking of support incidents, and service updates and upgrades. All other customer data, referred to as core customer data, is stored on-premises.

| Supporting services               | Customer data definition                      |
|---------------------------------------|----------------------------------------------------|
| Microsoft Dynamics Lifecycle Services | Project content and files are stored in a project. This includes application configuration data, code, metadata, and data assets that include the application and business process models. |
| Microsoft Office signup portal        | Customer information that is collected during the onboarding process.  |
| Microsoft Azure Active Directory      | Authentication for LCS and Azure DevOps.   |

Additional services or components can be configured to extend an on-premises deployment as needed; however, configuration choices may cause core customer data to be transferred outside of the customer’s data center. For example, configuring data management features that are used to integrate external services with an on-premises deployment may result in the transfer of core customer data outside the on-premises deployment.

## Next steps

After you’ve completed the planning activities mentioned in this article, you can begin the procedures listed in the [Onboard](on-premises-deployment-landing-page.md#onboard) section of the [On-premises deployment home page](on-premises-deployment-landing-page.md).

Be sure to refer to the [On-premises deployment home page](on-premises-deployment-landing-page.md) throughout your implementation for more information about planning, deployment, maintenance, and troubleshooting.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

