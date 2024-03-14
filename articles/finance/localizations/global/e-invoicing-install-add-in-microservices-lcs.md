---
title: Install the add-in for microservices in Lifecycle Services
description: This article explains how to install the Electronic Invoicing add-in in Microsoft Dynamics Lifecycle Services (LCS).
author: gionoder
ms.date: 02/11/2022
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: gionoder
ms.search.validFrom: 
ms.dyn365.ops.version: 
ms.custom: 
ms.assetid: 
ms.search.form: 
---

# Install the add-in for microservices in Lifecycle Services

[!include [banner](../../includes/banner.md)]

Authentication in the Electronic Invoicing service requires that you register your Microsoft Dynamics 365 Finance or Dynamics 365 Supply Chain Management environment in the services platform by installing the add-in for your environment in Microsoft Dynamics Lifecycle Services (LCS).

To register an environment, follow these steps.

1. Sign in to your LCS account.
2. On the project dashboard, select an LCS project.
2. In the project, on the **Environments** dashboard, select your deployed environment. The environment that you select must be running.
3. On the **Power Platform Integration** tab, in the **Environment add-ins** section, select **Install a new add-in**.
4. Select **Electronic Invoicing**.
5. In the **Microsoft Entra application ID** field, enter the fixed value **091c98b0-a1c9-4b02-b62c-7753395ccabe**. This value is always fixed. Make sure that you enter only a globally unique identifier (GUID). Don't include any other symbols, such as spaces, commas, periods, or quotation marks.
6. In the **Microsoft Entra tenant ID** field, enter the tenant ID of your Azure subscription account. The Microsoft Entra tenant that you specify should be the same tenant that is used for Regulatory Configuration Service (RCS).
7. Review the terms and conditions, and then select the checkbox.
8. Select **Install**. After a few minutes, the status should change from **Installing** to **Installed**. You might have to refresh the page to see this change.

Electronic invoicing is now ready to use.

> [!NOTE]
> Companies usually have several Finance or Supply Chain Management environments. These environments include production environments, User Acceptance Test (UAT) environments, and development (sandbox) environments. You must complete the preceding procedure for all environments that you want to connect to Electronic invoicing.