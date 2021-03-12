---
# required metadata
title: Provision Microsoft Teams from Dynamics 365 Commerce
description: This topic describes how to provision Microsoft Teams using organizational data from Dynamics 365 Commerce.
author: gvrmohanreddy
manager: annbe
ms.date: 03/12/2021
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

# Provision Microsoft Teams from Dynamics 365 Commerce

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic describes how to provision Microsoft Teams using organizational data from Dynamics 365 Commerce.

If you have not yet set up teams in Microsoft Teams for your retail stores, Dynamics 365 Commerce offers a way to provision Microsoft Teams easily. You can leverage well-defined information from Commerce such as organizational hierarchy, store names, employee information, and Azure Active Directory (Azure AD) accounts to use in Microsoft Teams to get your store employees started in Microsoft Teams.

Provisioning Microsoft Teams is a two-step process:

1. Create a team per each retail store and add store workers to their corresponding teams as members in Teams. If an employee is associated with two or more retail stores, team membership will reflect that. A communication team will be created to include regional managers as members to help publishing tasks from Microsoft Teams.  
1. Upload your organizational hierarchy from Commerce to Teams.  

## Provision Teams in Commerce headquarters

Before provisioning Teams, do the following:

- Confirm that all regional managers have been made communication managers.
- Confirm that all store managers and workers have their Azure AD accounts associated with their worker records in Commerce headquarters.

To provision Microsoft Teams in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Channel setup \> Microsoft Teams Integration Configuration**.
1. Select **Provision teams** on the Action Pane. A batch job named "Teams provision" will be created. 
1. Go to **System administration \> Inquiries \> Batch jobs** and find the most recent job that has the description "Teams provision." Wait until the execution of this job is completed.

> [!TIP]
> If you see the error "Failed to retrieve appliable Sku categories for the user," this indicates that none of your regional managers, store managers, and store workers have been associated with a Microsoft Teams license. To correct this error, select **Sync teams and members** on the Action Pane.  

<!-- ![Dynamics 365 Commerce - Teams integration configuration](media/D365-Commerce-Microsoft-Teams-Configuration_with_disclaimer.png)-->

## Verify teams provisioning in the Teams administrator portal

To verify teams provisioning in the Teams administrator portal, follow these steps.
	
1. Go to the [Teams administrator portal](https://admin.teams.microsoft.com/) and sign in as administrator of your e-commerce tenant. 
1. In the left navigation pane, select **Teams** to expand it, and then select **Manage teams*.
1. Confirm that one team per Commerce retail store has been created. 
1. Select a specific team and confirm that store workers have been added as members to the team. 
1. In the left navigation pane, select **Users**, and then confirm that all store employees across the stores have been added as users.

The following image shows an example of a **Manage teams** screen in Teams.

![Example of a Manage teams screen in Teams](media/Teams-FLW-Admin-Teams.png)

## Upload a Commerce organizational hierarchy to Teams 
	
The Commerce organizational hierarchy can be used in Microsoft Teams to publish tasks to all or selected stores that use the same hierarchy structure. 

To upload a Commerce organizational hierarchy to Teams, follow these steps.
	
1. In Commerce headquarters, go to **Retail and Commerce \> Channel setup \> Microsoft Teams Integration Configuration**.
1. Select **Download targeting hierarchy**, and then select **Retail Stores by Region** to download a CSV file of the organizational hierarchy. 
1. Install the Teams PowerShell module following the steps outlined in [Install Microsoft Teams PowerShell](https://docs.microsoft.com/microsoftteams/teams-powershell-install). 
1. In the PowerShell window, when prompted sign in using the administrator account for your Azure AD tenant.
1. Use the Teams Powershell module to upload the targeting hierarchy CSV file by following the steps in [Set up your team targeting hierarchy](https://docs.microsoft.com/microsoftteams/set-up-your-team-hierarchy). 

## Validate that the organizational hierarchy was uploaded to Teams

To validate that the organizational hierarchy was uploaded to Teams, follow these steps.

1. Sign in to **Teams** as a communication manager. 
1. In the left navigation pane, select **Tasks by Planner**.
1. Select the **Published lists** tab.
1. Create a new list with a dummy task.
1. Select **Publish**. You should now see the organizational hierarchy on the **Select who to publish to** dialog box, as shown in the following example image. 

![Publishing dialog box in Microsoft Teams](media/Microsoft-teams-verify-org-hierarchy.png)

## Additional resources

[Dynamics 365 Commerce and Microsoft Teams integration ](commerce-teams-integration.md)

[Synchronize task management between Microsoft Teams and POS](synchronize-tasks-teams-pos.md)

[Enable Microsoft Teams integration](enable-teams-integration.md)

[Manage user roles in Microsoft Teams](manage-user-roles-teams.md)


