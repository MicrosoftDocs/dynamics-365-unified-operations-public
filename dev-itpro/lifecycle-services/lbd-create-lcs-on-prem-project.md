---
# required metadata

title: Create an on-premises project in Lifecycle Services
description: This topic provides information about the process of setting up an on-premises project in Microsoft Dynamics Lifecycle Services (LCS). 
author: kfend
manager: AnnBe
ms.date: 06/09/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 60373
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: manado
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---
# Create an on-premises project in Lifecycle Services
You must use Microsoft Dynamics Lifecycle Services (LCS) to deploy and update an instance of Microsoft Dynamics 365 for Finance and Operations, Enterprise edition (on-premises). After you purchase a server and user license through the Volume Licensing flow or the Dynamics Purchase List flow, you will receive an email that includes instructions for signing in to LCS. A Microsoft Azure Active Directory (Azure AD) account is a prerequisite for signing in to LCS. Follow the instructions in <TODO – link to Shelly/Matthews doc> to create an Azure AD account or use an existing Azure AD account, and then complete all the sign-up steps. You will be redirected to LCS, where an on-premises implementation project will be provisioned for you.

 [![On-premises implementation project](./media/lbd-proejcts-01.png)](./media/lbd-proejcts-01.png)

The on-premises project has all the tools that you require in order to implement, maintain, and operate an on-premises solution. Here are some of the tools that are available in the on-premises project:

- **Methodology** – The on-premises methodology provides best practices that will help customers implement and manage on-premises projects.
- **Business process modeler** – Business process modeler (BPM) is used to capture requirements and do fit gap analysis.
- **Cloud-hosted environments** – Cloud-hosted environments are used to deploy developer and build topologies, and to complete Dev Application Lifecycle Management (ALM) for on-premises solutions.
- **Code upgrade** – These tools will help you upgrade code to a newer release.
- **Issue search** – Search for published KBs that are related to application and platform issues.
- **Localization and translation** – Localize and translate assets.
- **Support** – File and track support incidents.
- **Project users** – Assign users to a project.
- **Project settings** – Edit project-level settings, such as connectors, the project name, organization users, and the license number.
- **Asset library** – The Asset library is a library for various assets, such as packages.
- **SharePoint online library** – Connect to an online Microsoft SharePoint library.

To start your on-premises implementation, you must follow the steps in the methodology to correctly set up the project, deploy the developer and build environments, and then deploy sandbox and production environments. To help you with deployments, two environment slots are pre-allocated to the on-premises project. One slot is for a sandbox environment, and the other slot is for a production environment. These slots will be used during the Servicing flow to help guarantee that packages are tested in the sandbox environment before they are applied in the production environment.
