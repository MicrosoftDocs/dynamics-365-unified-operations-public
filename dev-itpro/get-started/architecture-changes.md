---
# required metadata

title: Architecture changes in Dynamics 365 for Operations | Microsoft Docs
description: The application stack of Microsoft Dynamics AX has been divided into three separate models: Application Platform, Application Foundation, and Application Suite. 
author: RobinARH
manager: AnnBe
ms.date: 2016-02-08 23:21:51
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: RobinARH
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 31751
ms.assetid: ab0dd748-8aba-40e9-bc89-91064901cb3b
ms.region: Global
# ms.industry: 
ms.author: robinr

---

# Architecture changes in Dynamics 365 for Operations

The application stack of Microsoft Dynamics AX has been divided into three separate models: Application Platform, Application Foundation, and Application Suite. 

Overview
--------

There have been some changes in the application stack and server architecture to align with the three key pillars in Microsoft Dynamics AX:

-   New client
-   Cloud readiness
-   New development stack

The application stack has been divided into three separate models: Application Platform, Application Foundation, and Application Suite. The separation enables new application development on the base foundation models, just as the Fleet Management sample application has been developed. Note the following important points about the changes in the server architecture:

-   The services endpoint on the server is now responsible for returning all form and control metadata and data to the browser-based client. There is no longer any remote procedure call (RPC)-based communication with the server. The form objects still run on the server, and rendering has been optimized for browsers and other clients through server and client-side (browser) investments.
-   The server, including the application code base, is deployed to an Internet Information Services (IIS) web application. In the cloud, it's deployed to Microsoft Azure infrastructure as a service (IaaS) virtual machines (VMs).
-   Dynamics AX is hosted on Azure and is available for access through the Internet. A user can use a combination of clients and credentials to access it. The recommended primary identity provider is OrgID, and the store for the identity is Azure Active Directory (Azure AD). The security subsystem uses the same AuthZ semantics for users and roles.
-   Two types of clients must be considered for access to Dynamics AX in the cloud: active clients and passive clients.
    -   Active clients can programmatically initiate actions based on responses from the server. An active client doesn't rely on HTTP redirects for authentication. A smart/rich client is an example of an active client.
    -   Passive clients can't programmatically initiate actions based on responses from the server. A passive client relies on HTTP redirects for authentication. A web browser is an example of a passive client.

    Currently, Access Control Service (ACS) doesn't support a mechanism for non-interactive authentication. Therefore, even when active clients try to authenticate against Dynamics AX by using ACS, they must use passive client authentication, in which a browser dialog box prompts the user to enter his or her credentials.
-   A completely revamped metadata subsystem incorporates the new compiler and Microsoft Visual Studio–based development model. The model store is represented as a set of folders and XML artifacts that are organized by model. Dynamics AX model elements, such as tables, forms, and classes, are represented by an XML file that contains both metadata and source code.

The left side of the following diagram shows how the application stack has been split into distinct models. The right side shows how the key components are stacked in the server. [![](./media/architecturedrawing1.png)](./media/architecturedrawing1.png)   Microsoft Dynamics AX 2012 unionizes permissions that are granted to a user. However, an issue can occur when a data source is granted read permissions through an entry point and edit permissions through a form. Because permissions are unionized, the user eventually has edit permissions to that data source in this case. However, if the form was granted read access through a menu item, the expectation is that the data source can't be edited through that path. Therefore, the context of the call isn't honored. In Dynamics AX, the context of the call is honored, based on the permissions that are granted through the entry point. If the form was granted read access through a menu item, the framework grants the user only read access to the table. However, if the same form is opened through another menu item that provides write access, the form is granted write permissions. This behavior simplifies the development experience, because developers can specify the desired behavior for a form through a given entry point.

## Cloud architecture
The cloud architecture includes services that automate software deployment and provisioning, operational monitoring and reporting, and seamless application lifecycle management. The cloud architecture consists of three main conceptual areas:

-   **Microsoft Dynamics Lifecycle Services (LCS)** – LCS is a multi-tenant shared service that enables a wide range of lifecycle-related capabilities for Microsoft Dynamics AX. Capabilities that are specific to this release include software development, customer provisioning, service level agreement (SLA) monitoring, and reporting capabilities.
-   **Microsoft Dynamics AX **– Dynamics AX VM instances are deployed through LCS to your Azure subscription. Various topologies are available: demo, development/test, and high-availability production topologies.
-   **Shared Microsoft services** – Dynamics AX uses several Microsoft services to enable a “One Microsoft” solution where customers can manage a single sign-in, subscription management, and billing relationship with Microsoft across Dynamics AX, Microsoft Office 365, and other online services.

Dynamics AX uses many features of the Azure platform, such as Microsoft Azure Storage, networking, monitoring, and SQL Azure, to name a few.  Shared services put into operation and orchestrate the application lifecycle of the Dynamics AX environments for participants. Together, Azure functionality and LCS that are built for Dynamics AX will offer a robust cloud service.

## Development environment
The architecture of a Dynamics AX development environment resembles the architecture of the Dynamics AX cloud instance. It also includes the Dynamics AX software development kit (SDK), which consists of the Visual Studio development tools and other components. Source control through Team Foundation Server or Visual Studio Online enables multiple-developer scenarios, where each developer uses his or her own Dynamics AX development environment. Deployment packages can be compiled and generated on a development environment and deployed to cloud instances by using LCS. The following diagram shows how the key components interact in a Dynamics AX development environment.[![CloudEnvironmentTechConcepts](./media/cloudenvironmenttechconcepts.png)](./media/cloudenvironmenttechconcepts.png)

