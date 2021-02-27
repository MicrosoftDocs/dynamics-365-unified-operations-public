
---
# required metadata
title: Provision Microsoft Teams from Dynamics 365 Commerce
description: This topic describes how to provision Microsoft Teams using organizational data from Dynamics 365 Commerce.
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

# Provision Microsoft Teams from Dynamics 365 Commerce

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic describes how to provision Microsoft Teams using organizational data from Dynamics 365 Commerce.

If you have not setup teams in Microsoft Teams for you retail stores yet, Dynamics 365 Commerce offers a way to provision Microsoft Teams easily.  You can leverage well defined information from Dynamics 365 Commerce such as your organization hierarchy, stores names, employees AAD accounts to Microsoft Teams so that your store employees can jump start in Microsoft Teams.

Provisioning Microsoft Teams is two step process as follows:

1. Create a team per retail store and add store workers to corresponding team as members in Microsoft Teams.  If an employee is associated with two or more retail stores, team(s) membership also will reflect the same.  A Communication team will be created additionally to include regional managers as member to help publishing tasks from Microsoft Teams.  Refer to how to make regional managers as communication manager. 
2. A way to upload your organization hierarchy from Dynamics 365 Commerce to Microsoft Teams.  

## Provision Microsoft Teams

1. Make sure Regional Managers are made as Communication Managers. Refer to how to make…..
2. Make sure all store managers and store workers have AAD identify associated with worker record in the HQ. Refer to how to….
3. Go to Retail and Commerce > Channel setup > Microsoft Teams Integration Configuration:
	a. Click *Provision teams* on the menu bar.
	b. Notice that a batch job called *Teams provision* will be created. 
	c. Go to System administration > Inquiries > Batch jobs, find the last job which job description is Teams provision. Wait until when this job is ended.

> [!TIP]
> If you run into the error "Failed to retrieve appliable Sku categories for the user" which indicates that none of your store managers, store workers and regional managers have Microsoft Teams license associated.  Pl double and start *Sync teams and members* .  

![Dynamics 365 Commerce - Teams integration configuration](media/D365-Commerce-Microsoft-Teams-Configuration_with_disclaimer.png)

##Verify teams provisioning in Teams admin portal
	
1. Go to https://admin.teams.microsoft.com/
2. Login as tenants admin 
3. Click *Teams* on the menu to expand, then click on *Manage teams*.
4. Notice that a team per retail store from Dynamics 365 commerce has been created. 
5. Click a specific team and notice that store workers from workbook have been added as members under the team in Teams. 
6. Click *Users* on the menu and notice that all store employees across the stores are being added as users.

![Dynamics 365 Commerce - Provisioning teams from Dynamics 365 Commerce](media/Teams-FLW-Admin-Teams.png)

## Upload organization hierarchy to Microsoft Teams. 
	
The organization hierarchy from Dynamics 365 Commerce can be leveraged in Microsoft Teams for publishing tasks to all or selected stores using the same hierarchy structure. 
	
1. Go to Retail and Commerce > Channel setup > Microsoft Teams Integration Configuration
2. Click *Download targeting hierarchy* and select *Retail Stores by Region* to download the CSV file of targeting hierarchy. 
3. Install *Teams Powershell module* per steps outlined @ https://docs.microsoft.com/en-us/microsoftteams/teams-powershell-install.  
4. Use *Teams Powershell module* to upload the targeting hierarchy using CSV file downloaded with hierarchy by following this guideline: https://docs.microsoft.com/en-us/microsoftteams/set-up-your-team-hierarchy. 
		a. Login using your Azure admin account for your tenant 

## Validate Hierarchy uploaded in Microsoft Teams

1. Go to Microsoft *Teams* application 
2. Login as communication manager 
3. Launch *Tasks by Planner* app
4. Click on *Published lists* tab
5. Create a *new list* with a dummy task.
6. Click Publish button 

You will see organization hierarch on the publish dialog similar to below picture: 

![Dynamics 365 Commerce - Provisioning teams from Dynamics 365 Commerce](media/Microsoft-teams-verify-org-hierarchy.png)

## Additional resources

[Dynamics 365 Commerce and Microsoft Teams integration ](commerce-teams-integration.md)

[Synchronize task management between Microsoft Teams and POS](synchronize-tasks-teams-pos.md)

[Configure Microsoft Teams integration](configure-teams-integration.md)

[Manage user roles in Microsoft Teams](manage-user-roles-teams.md)


