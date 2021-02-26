---
# required metadata
title: Configure Microsoft Teams integration
description: This topics descibes how to opt-in and opt-out of Dynamics 365 Commerce and Microsoft Teams integration.
author: gvrmohanreddy
manager: annbe
ms.date: 03/01/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
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

# Configure Microsoft Teams integration 

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topics descibes how to opt-in and opt-out of Dynamics 365 Commerce and Microsoft Teams integration.

In order to provision Microsoft Teams with information from Dynamics 365 Commerce and synchronize the task management features between Teams and the point of sale (POS) application, you must enable the integration features in Dynamics 365 Commerce headquarters. 

> [!NOTE]
> When you enable Microsoft Teams integration, you consent to share your data with Microsoft Teams. Data shared with Microsoft Teams may reside in a different geography than your Dynamics 365 Commerce data and may be subject to different compliance standards. For more information, see [Microsoft Trust Center](https://www.microsoft.com/trust-center). For information about Microsoft privacy policies, see the [Microsoft Privacy Statement] (http://aka.ms/privacy).

## Enable Microsoft Teams integration 

To enable Teams integration with Dynamics 365 Commerce, you must first register the Teams application with your tenant at the Azure portal.

To register the Teams application with your tenant at the Azure portal, follow these steps.

1. Go through Quickstart: Register an app in the Microsoft identity platform to register Microsoft Teams application with your tenant at Azure portal
1. After registering Microsoft Teams, per Register an application process,  retrieve Application ID from overview section in Azure Portal 
1. Add a client secret per Add credentials process and retrieve the application key. 

To enable Microsoft Teams integration in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Channel setup \> Microsoft Teams Integration Configuration**.
1. Select **Edit** on the Action Pane.
1. Set **Enable Microsoft Teams Integration** to **Yes**.
1. For **Application ID** and **Application Key**, enter the values you have obtained from steps 2 and 3 above. 
1. Select **Save** on the Action Pane.

![Dynamics 365 Commerce - Teams integration configuration](media/D365-Commerce-Microsoft-Teams-Configuration_with_disclaimer.png)

## Disable Microsoft Teams integration 

To stop using Microsoft Teams integration with Dynamics 365 Commerce, follow these steps.

1. Go to **Retail and Commerce \> Channel setup \> Microsoft Teams Integration Configuration**.
2. Select **Edit** on the Action Pane.
3. Set the **Enable Microsoft Teams Integration** option to **No**.
4. For **Application ID** and **Application Key**, delete the values entered when enabling. 
5. Select **Save** on the Action Pane.

> [!NOTE]
> Once you disable Teams integration with Commerce, POS terminals will no longer show tasks published from the Teams application. 

## Additional resources

[Dynamics 365 Commerce and Microsoft Teams integration ](commerce-teams-integration.md)

[Provision Microsoft Teams from Dynamics 365 Commerce](provision-teams-from-commerce.md)

[Synchronize task management between Microsoft Teams and POS](synchronize-tasks-teams-pos.md)

[Manage user roles in Microsoft Teams](manage-user-roles-teams.md)
