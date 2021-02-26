---
# required metadata
title: Manage user roles in Microsoft Teams
description: This topic covers how to manage Dynamics 365 Commerce user roles in Microsoft Teams.
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

# Manage user roles in Microsoft Teams

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic covers how to manage Dynamics 365 Commerce user roles in Microsoft Teams.

As you create a team per store or channel in Microsoft Teams, there is a group membership corresponding to the team is created, for example `HOUSTON_D365@<YourTenantAADDomain>.com` for a Houston e-commerce store team. All the store workers under a team group membership will be assigned with one of two user roles: "owner" or "member." A store employee with the "owner" user role, typically a store manager, can do operations like adding a private channel or adding members. 

The following example image of Microsoft Teams shows a list of team members and their user roles.

![Dynamics 365 Commerce and Teams integration - User Roles](media/d365-commerce-teams-integration-user-roles.png)

For more information, see [Assign team owners and members in Microsoft Teams](https://docs.microsoft.com/microsoftteams/assign-roles-permissions).

## FAQ

#### How do you assign the "owner" role to a user while provisioning Microsoft Teams from Dynamics 365 Commerce? 

All people with Store Managers role will be added as an owner to the corresponding team's group members.  E.g. store managers of Houston will be added as owners to HOUSTON_D365@<TenantAADDomain>.com) so that store managers can perform operations like adding a member of deleting a member from the group as needed. 

#### What happens if a store doesn't a store managers?

Group will not created, means not team for the store in the Teams as well. 

#### What happens if store managers leave the company?

Add new Store Manager in the HQ and re-provision Teams so that new manager will have required privilege's in the Teams for the group. 

#### How to clear the graph API token stored in the session storage?

User who logs in into POS with AAD account to view the tasks, should logout  from POS or close the application to invalidate the session storage. 

## Additional resources

[Dynamics 365 Commerce and Microsoft Teams integration ](commerce-teams-integration.md)

[Provision Microsoft Teams from Dynamics 365 Commerce](provision-teams-from-commerce.md)

[Synchronize task management between Microsoft Teams and POS](synchronize-tasks-teams-pos.md)

[Configure Microsoft Teams integration](configure-teams-integration.md)
