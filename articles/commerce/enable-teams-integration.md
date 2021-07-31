---
# required metadata
title: Enable Dynamics 365 Commerce and Microsoft Teams integration
description: This topic describes how to enable Microsoft Dynamics 365 Commerce and Microsoft Teams integration.
author: gvrmohanreddy
ms.date: 03/31/2021
ms.topic: article
ms.prod: 
ms.technology: 
# optional metadata
# ms.search.form: 
#ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: gmohanv
ms.search.validFrom: 2021-01-15
ms.dyn365.ops.version: 10.0.18
---

# Enable Dynamics 365 Commerce and Microsoft Teams integration

[!include [banner](includes/banner.md)]

This topic describes how to enable Microsoft Dynamics 365 Commerce and Microsoft Teams integration.

To provision Teams with information from Dynamics 365 Commerce and synchronize the task management features between Teams and the point of sale (POS) application, you must enable the integration features in Commerce headquarters.

> [!NOTE]
> When you enable Teams integration, you consent to share your data with Teams. Data that is shared with Teams might reside in a different country than your Commerce data, and it might be subject to different compliance standards. For more information, see the [Microsoft Trust Center](https://www.microsoft.com/trust-center). For information about Microsoft privacy policies, see the [Microsoft Privacy Statement](https://aka.ms/privacy).

## Enable Teams integration

Before you can enable Microsoft Teams integration with Commerce, you must register the Teams application with your tenant in the Azure portal.

To register the Teams application with your tenant in the Azure portal, follow these steps.

1. Follow the steps in [Quickstart: Register an app in the Microsoft identity platform](/azure/active-directory/develop/quickstart-register-app) to register the Teams application with your tenant in the Azure portal.
1. Copy the **Application (client) ID** value from the **Overview** page for the registered app. You will use this value to enable Teams integration in Commerce headquarters.
1. Copy the certificate value that was entered when you [added a certificate](/azure/active-directory/develop/quickstart-register-app#add-a-certificate) in step 1. The certificate is also known as the public key or application key. You will use this value to enable Teams integration in Commerce headquarters.

To enable Teams integration in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Channel setup \> Microsoft Teams integration configuration**.
1. On the Action Pane, select **Edit**.
1. Set the **Enable Microsoft Teams integration** option to **Yes**.
1. In the **Application ID** and **Application key** fields, enter the values you obtained when you registered the Teams application in the Azure portal.
1. On the Action Pane, select **Save**.

The following illustration shows an example of the configuration of Teams integration in Commerce headquarters.

![Teams integration configuration in Commerce headquarters.](media/D365-Commerce-Microsoft-Teams-Configuration_with_disclaimer.png)

## Disable Teams integration

To disable Microsoft Teams integration in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Channel setup \> Microsoft Teams Integration Configuration**.
1. On the Action Pane, select **Edit**.
3. Set the **Enable Microsoft Teams integration** option to **No**.
4. Clear the values from the **Application ID** and **Application Key** fields.
1. On the Action Pane, select **Save**.

> [!NOTE]
> After you disable Teams integration with Commerce, POS terminals will no longer show tasks that are published from the Teams application.

## Additional resources

[Dynamics 365 Commerce and Microsoft Teams integration overview](commerce-teams-integration.md)

[Provision Microsoft Teams from Dynamics 365 Commerce](provision-teams-from-commerce.md)

[Synchronize task management between Microsoft Teams and Dynamics 365 Commerce POS](synchronize-tasks-teams-pos.md)

[Manage user roles in Microsoft Teams](manage-user-roles-teams.md)

[Map stores and teams if there are pre-existing teams in Microsoft Teams](map-stores-existing-teams.md)

[Dynamics 365 Commerce and Microsoft Teams integration FAQ](teams-integration-faq.md)