---
# required metadata

title: Microsoft Dynamics 365 for Finance and Operations Architecture
description: This topic provides an overview of the architecture of Microsoft Dynamics 365 for Finance and Operations.
author: ClaudiaBetz-Haubold
manager: AnnBe
ms.date: 05/33/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 56551
ms.assetid: d876e8de-d547-43e5-9259-f095821dc758
ms.search.region: Global
# ms.search.industry: 
ms.author: chaubold
ms.search.validFrom: 2018-05-30
ms.dyn365.ops.version: AX 7.0.0

---

# Microsoft Dynamics 365 for Finance and Operations Architecture

[!include [banner](../includes/banner.md)]

The Microsoft Dynamics 365 for Finance and Operations cloud architecture includes services that automate software deployment and provisioning, operational monitoring and reporting, and seamless application lifecycle management.

![Cloud architecture](..media/cloud-architecture.png)

The Microsoft Dynamics 365 for Finance and Operations cloud architecture consists of these conceptual areas:

  - **Subscription** – A subscription to Microsoft Dynamics 365 for Finance and Operations (cloud) gives you an online cloud environment(s) and experience. 
  - **Licenses** – Customers must purchase Subscription Licenses (SLs) for their organization or their affiliates’ employees and on-site agents, vendors or contractors who directly or indirectly access Microsoft Dynamics 365 for Finance and Operations. Microsoft Dynamics 365 for Finance and Operations is licensed through the Microsoft Volume Licensing (VL) and the Cloud Solution Provider Program (CSP), for more information download the latest Microsoft Dynamics 365 Licensing Guide from Dynamics 365 pricing
  - **Tenant** - In Azure Active Directory (Azure AD), a tenant is representative of an organization. It is a dedicated instance of the Azure AD service that an organization receives and owns when it creates a relationship with Microsoft, such as by signing up for a Microsoft cloud service like Azure, Microsoft Intune, or Office 365. Each Azure AD tenant is distinct and separate from other Azure AD tenants. See How to get an Azure Active Directory Tenant.
  A tenant houses the users in a company and the information about them - their passwords, user profile data, permissions, and related information. It also contains groups, applications, and other information pertaining to an organization and its security.
  The tenant is created when a customer signs up for their first subscription of any Microsoft Online Service, such as Microsoft Office 365, Microsoft Dynamics 365, Microsoft Azure, or any other online service. Subsequently, more subscriptions of the same or other Microsoft Online Services can be grouped within the same tenant.
  An organization can have multiple AAD tenants. If that is the case, it is important to ensure that the subscriptions for Microsoft Dynamics 365 for Finance and Operations are associated with the correct tenant.
  - **Microsoft Azure Active Directory** –  Microsoft Azure Active Directory (Azure AD) is Microsoft’s multi-tenant, cloud-based directory and identity management service that combines core directory services, application access management, and identity protection into a single solution, for more information see Azure Active Directory Documentation. Microsoft Dynamics 365 for Finance and Operations is using Azure AD as the store for identity. Access to Azure AD comes as part of a subscription to Microsoft Dynamics 365 for Finance and Operations.
  - **Microsoft Office 365 admin center** – Office 365 admin center is the subscription management portal that Office 365 provides for administrators. Office 365 admin center is used to provide management functions for users (Azure AD) and subscriptions, including information about service health. For more information see About the Office 365 admin center 
Note: No Office 365 licenses are needed to deploy Microsoft Dynamics 365 for Finance and Operations however you might need them for specific Office integration scenarios. For more information see Office integration
  - **Lifecycle Services (LCS)** – Lifecycle Services (LCS) for Microsoft Dynamics is a collaboration portal that provides an environment and a set of regularly updated services that can help you manage the application lifecycle of your Microsoft Dynamics 365 for Finance and Operations implementations. for more information see Lifecycle Services for Finance and Operations. After you've purchased and activated a subscription to Microsoft Dynamics 365 for Finance and Operations, an implementation project workspace is provisioned in LCS when the tenant administrator signs in for the first time.
  >[!Note]
  > An implementation project is an LCS project for the Microsoft-managed Dynamics 365 for Finance and Operations cloud service. As a Microsoft partner, you can also provision non-implementation LCS projects for your own purposes; see Lifecycle Services for Finance and Operations partners. 
  - **Microsoft Dynamics 365 for Finance and Operations** – Microsoft Dynamics 365 for Finance and Operations is deployed through Lifecycle Services LCS. Various topologies are available: development/test/build, acceptance test, performance test and high-availability production. For more information about different topologies download the latest Microsoft Dynamics 365 Licensing Guide from Dynamics 365 pricing
  - **Visual Studio Team Services (VSTS)** – Visual Studio Team Services (VSTS) is primarily used for code version control and deploying a build environment. Other purposes are tracking of support incidents as work items in VSTS submitted to Microsoft through Cloud Powered Support, Integration of the Business Process Modeler (BPM) library hierarchy into your VSTS project as a hierarchy of work items. VSTS is also used during code upgrade.

Under the hood many features of the Azure platform are used, such as Microsoft Azure Storage, networking, monitoring, and SQL Azure, to name a few. Shared services put into operation and orchestrate the application lifecycle of the environments for participants. Together, Azure functionality and Lifecycle Services (LCS) will offer a robust cloud service.

  >[!Note]
  > Although many features of Azure platform are used you don’t need an Azure subscription to deploy Microsoft Dynamics 365 for Finance and Operations in Microsoft Managed cloud. You only need an Azure subscription to deploy Microsoft Dynamics 365 for Finance and Operations cloud-hosted environments into your own Azure subscription.



