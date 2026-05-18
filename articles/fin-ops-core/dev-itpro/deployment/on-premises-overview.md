---
title: On-premises deployment overview
description: Dynamics 365 Finance + Operations (on-premises) supports running business processes in customer data centers, including overviews of architecture and data storage.
author: faix
ms.author: osfaixat
ms.topic: overview
ms.custom: 
  - bap-template
ms.date: 04/02/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: Platform Update 8
ms.service: dynamics-365-op
---
# On-premises deployment overview

[!include [banner](../includes/banner.md)]

Microsoft Dynamics 365 Finance + Operations (on-premises) supports running business processes in customer data centers. With this deployment option, application servers and the Microsoft SQL Server database run in the customer’s data center. Customers and partners use Microsoft Dynamics Lifecycle Services to manage their on-premises deployments. Lifecycle Services is an application management portal that provides tools and services for managing the application lifecycle of your implementations in the cloud and on-premises. Lifecycle Services features, such as business process modeling, software deployment and patching, and monitoring and diagnostics, help support on-premises deployments.

> [!IMPORTANT]
> Dynamics 365 Finance + Operations (on-premises) isn't supported on any public cloud infrastructure, including Microsoft Azure Cloud services. However, it's supported to run on [Microsoft Azure Stack HCI](https://azure.microsoft.com/products/azure-stack/hci/) and [Microsoft Azure Stack Hub](https://azure.microsoft.com/products/azure-stack/hub/).

## Architecture

The on-premises deployment option uses cloud components running on-premises by using Microsoft Azure Server Service Fabric standalone clusters. Service Fabric is the next-generation Microsoft middleware platform for building and managing enterprise-class high-scale applications. You can deploy Service Fabric standalone clusters on any computer that's running Windows Server.

On-premises deployment defines two types of Service Fabric standalone clusters: clusters for production environments and clusters for sandbox environments. You deploy the following roles or node types into both types of clusters:

- Application Object Servers (AOS) – Provides the ability to run the application functionality in client and batch.
- SQL Server Integration Services (SSIS) – Provides import/export scenarios functionality as part of the Data Management Framework (DMF\DIXF).
- Management Reporter (MR) – Provides financial reporting functionality.
- SQL Server Reporting Services (SSRS) – Provides document reporting functionality.
- Environment Orchestrator – Enables on-premises environment management from Lifecycle Services.

Figure 1 shows a logical diagram of the node types deployed in a Service Fabric standalone cluster.

:::image type="content" source="./media/on-premises-overview-01.png" alt-text="Screenshot of Service fabric standalone cluster.":::

You orchestrate application lifecycle management for on-premises deployments through Lifecycle Services. Use the proven tools and methodologies in Lifecycle Services to help manage your on-premises deployments (Figure 2). The development experience continues to be the same as in cloud deployments through 1-box VHDs.

:::image type="content" source="./media/on-premises-overview-02.png" alt-text="Screenshot of Application lifecycle management for Local Business Data deployments.":::

## Data storage

The on-premises deployment option stores core customer data on-premises. Core customer data is a subset of the customer data definition provided in the [Microsoft Trust Center](https://www.microsoft.com/trustcenter/privacy/how-microsoft-defines-customer-data). Table 1 outlines the categories of customer data that services such as Lifecycle Services, Microsoft Entra ID, and Microsoft Office sign up portal store in Microsoft Azure data centers located in the United States. All other customer data, referred to as core customer data, is stored on-premises.  

Table 1: Customer data stored in Microsoft Azure data centers located in the United States by services supporting on-premises environments. These services enable initial onboarding, initiation, and tracking of support incidents, and service updates and upgrades.  

| Supporting services                   | Customer data definition                                                    |
|---------------------------------------|---------------------------------------------------------------------------------------------|
| Microsoft Dynamics Lifecycle Services | Project content and files are stored in a project. This storage includes application configuration data, code, metadata, and data assets that comprise the application and business process models. Also included are anonymized user activity logs and information that is collected during the onboarding process. |
| Microsoft Office sign up portal        | Customer information that is collected during the onboarding process.                     |
| Microsoft Entra ID      | Authentication for Lifecycle Services and Azure DevOps.                                        |
  
You can configure additional services or components to extend an on-premises deployment as needed. However, some configuration choices might transfer core customer data outside of the customer’s data center. For example, configuring data management features that are used to integrate external services with an on-premises deployment might result in the transfer of core customer data outside the on-premises deployment.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
