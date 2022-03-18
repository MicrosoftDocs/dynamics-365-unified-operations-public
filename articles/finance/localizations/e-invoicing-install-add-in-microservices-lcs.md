---
# required metadata

title: Install the add-in for microservices in Lifecycle Services
description: This topic explains how to install the Electronic Invoicing add-in in Microsoft Dynamics Lifecycle Services (LCS).
author: dkalyuzh
ms.date: 02/11/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkalyuzh
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Install the add-in for microservices in Lifecycle Services

[!include [banner](../includes/banner.md)]

Authentication in the Electronic Invoicing service requires that you register your Microsoft Dynamics 365 Finance or Dynamics 365 Supply Chain Management environment in the services platform by installing the add-in for your environment in Microsoft Dynamics Lifecycle Services (LCS).

To register an environment, follow these steps.

1. Sign in to your LCS account.
2. On the project dashboard, select an LCS project.
2. In the project, on the **Environments** dashboard, select your deployed environment. The environment that you select must be running.
3. On the **Power Platform Integration** tab, in the **Environment add-ins** section, select **Install a new add-in**.
4. Select **Electronic Invoicing**.
5. In the **AAD application ID** field, enter **091c98b0-a1c9-4b02-b62c-7753395ccabe**. This value is a fixed value. Make sure that you enter only a globally unique identifier (GUID). Don't include any other symbols, such as spaces, commas, periods, or quotation marks.
6. In the **AAD tenant ID** field, enter the tenant ID of your Azure subscription account. The Azure Active Directory (Azure AD) tenant that you specify should be the same tenant that is used for Regulatory Configuration Service (RCS).
7. Review the terms and conditions, and then select the checkbox.
8. Select **Install**. After a few minutes, the status should change from **Installing** to **Installed**. You might have to refresh the page to see this change.

Electronic invoicing is now ready to use.

> [!NOTE]
> Companies usually have several Finance or Supply Chain Management environments. These environments include production environments, User Acceptance Test (UAT) environments, and development (sandbox) environments. You must complete the preceding procedure for all environments that you want to connect to Electronic invoicing.
