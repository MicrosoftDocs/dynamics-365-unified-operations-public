---
# required metadata

title: Install the add-in for microservices in Lifecycle Services
description: This topic provides information about how to install the Electronic Invoicing add-in in Lifecycle Services.
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

Authentication in the Electronic invoicing service requires that you register your Dynamics 365 Finance or Dynamics 365 Supply Chain Management environment in the services platform by installing the add-in for your environment in Lifecycle Services (LCS). 

To register, complete the following steps.

1. Sign in to your LCS account, and on the project dashboard, select an LCS project.
2. In the project, on the **Environments** dashboard, select your deployed environment. The environment that you select must be running.
3. On the **Power Platform Integration** tab, in the **Environment add-ins** field group, select **Install a new add-in**.
4. Select **Electronic Invoicing**.
5. In the **AAD application ID** field, enter ***091c98b0-a1c9-4b02-b62c-7753395ccabe***. This is a fixed value. Make sure that only the GUID is entered, and you don't enter any other symbols such as a space, comma, dot, or quotes.
6. In the **AAD tenant ID** field, enter the tenant ID of your Azure subscription account. The Azure Active Directory (Azure AD) tenant that you specify should be the same tenant that is used for the Regulatory Configuration Service (RCS).
7. Review the terms and conditions, and then select the check box.
8. Select **Install**. After a few minutes, the status should change from **Installing** to **Installed**. You might have to refresh the page to see this change. After this, Electronic Invoicing is ready to use.



>	[!NOTE]
> Companies usually have several Finance or Supply Chain management environments that include a Production environment, a User Acceptance Test (UAT) environment, and a Development (sandbox) environment. Perform these steps with all environments that you want to connect to Electronic invoicing.


