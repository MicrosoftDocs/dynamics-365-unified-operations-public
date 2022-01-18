---
# required metadata

title: Install the add-in for microservices in Lifecycle Services
description: This topic provides description of the process of installation Electronic invoicing Add-in in LCS.
author: dkalyuzh
ms.date: 12/15/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata
---

[!include [banner](../includes/banner.md)]

Authentication in the Electronic invoicing requires registering Finance and Operations environments in the services platform by mean of installing add-in for your environment in LCS. To get registered you should do the next steps:
1. Sign in to your LCS account, and on the LCS project dashboard, select an LCS project.
2. In the project, on the **Environments** dashboard, select your deployed environment. The environment that you select must be running.
3. On the **Power Platform Integration** tab, in the **Environment add-ins** field group, select **Install a new add-in**.
4. Select **Electronic Invoicing**.
5. In the **AAD application ID** field, enter ***091c98b0-a1c9-4b02-b62c-7753395ccabe***. This is a fixed value. Make sure that only GUID is entered, and you don't enter any other symbols like space, comma, dot, quotes, etc.
6. In the **AAD tenant ID** field, enter the tenant ID of your Azure subscription account. The Azure Active Directory (Azure AD) tenant that you specify should be the same tenant that is used for Regulatory Configuration Services (RCS).
7. Review the terms and conditions, and then select the check box.
8. Select **Install**. After a few minutes, the status should change from Installing to Installed. You might have to refresh the page to see this change.

At that point, Electronic Invoicing is ready to use.



>	[!NOTE]
> Usually all companies have several Finance or Supply Chain management environments that include Production environment, User Acceptance Test (UAT) environment, and Development (sandbox) environment. You need to perform this operation with all environments that you want to connect to Electronic invoicing.

