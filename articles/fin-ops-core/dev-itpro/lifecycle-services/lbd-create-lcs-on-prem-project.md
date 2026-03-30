---
title: Set up on-premises projects in Lifecycle Services (LCS)
description: Learn about the process of setting up an on-premises project in Microsoft Dynamics Lifecycle Services (LCS), including environment limits. 
author: PeterRFriis
ms.author: peterfriis
ms.topic: article
ms.custom: 
  - bap-template
ms.date: 03/06/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
search.app:
  - financeandoperationsonprem-docs
ms.service: dynamics-365-op
---

# Set up on-premises projects in Lifecycle Services (LCS)

[!include [banner](../includes/banner.md)]
[!include [LCS freeze](../../../includes/lcs-freeze-banner.md)]

You must use Microsoft Dynamics Lifecycle Services (LCS) to deploy and update an instance of Dynamics 365 Finance + Operations (on-premises). After you purchase a server and user license through the Volume Licensing flow or the Dynamics Price List flow, see the article [Buy Finance + Operations (on-premises)](../../fin-ops/get-started/purchase-on-premises.md) to create a Microsoft Entra account or use an existing Microsoft Entra account, and then complete all the sign-up steps. You are redirected to LCS, where an on-premises implementation project is provisioned for you.

:::image type="content" source="./media/lbd-proejcts-01.png" alt-text="Screenshot of an on-premises implementation project.":::

The on-premises project has all the tools that you require to implement, maintain, and operate an on-premises solution. Here are some of the tools that are available in the on-premises project:

- **Methodology** – The on-premises methodology provides best practices that help customers implement and manage on-premises projects.
- **Business process modeler** – Use the business process modeler (BPM) to capture requirements and do fit gap analysis.
- **Cloud-hosted environments** – Use cloud-hosted environments to deploy developer and build topologies, and to complete Dev Application Lifecycle Management (ALM) for on-premises solutions.
- **Code upgrade** – These tools help you upgrade code to a newer release.
- **Issue search** – Search for published KBs that are related to application and platform issues.
- **Localization and translation** – Localize and translate assets.
- **Support** – File and track support incidents.
- **Project users** – Assign users to a project.
- **Project settings** – Edit project-level settings, such as connectors, the project name, organization users, and the license number.
- **Asset library** – The Asset library is a library for various assets, such as packages.
- **SharePoint online library** – Connect to an online Microsoft SharePoint library.

To start your on-premises implementation, follow the steps in the methodology to correctly set up the project, deploy the developer and build environments, and then deploy sandbox and production environments. To help you with deployments, the on-premises project preallocates two environment slots. One slot is for a sandbox environment, and the other slot is for a production environment. Use these slots during the Servicing flow to help guarantee that you test packages in the sandbox environment before you apply them in the production environment.

## Environment limits
You can deploy only a limited number of specific environment types in an on-premises project. The following table outlines these limits.

|Organization type|Production environments|Sandbox environments|
|-----------------|-----------------------|--------------------|
| Customer | 1 | 1 or more |
| Partner (with on-premises license) | 1 | 1 or more |
| Partner (without on-premises license) | 0 | 1 |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
