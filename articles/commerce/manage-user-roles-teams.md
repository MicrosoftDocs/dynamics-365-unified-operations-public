---
# required metadata
title: Manage user roles in Microsoft Teams
description: This topic covers how to manage Dynamics 365 Commerce user roles in Microsoft Teams, and provides answers to frequently asked questions.
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

This topic covers how to manage Dynamics 365 Commerce user roles in Microsoft Teams, and provides answers to frequently asked questions.

As you create a team per store or channel in Microsoft Teams, a group membership corresponding to the team is created, for example `HOUSTON_D365@<YourTenantAADDomain>.com`. All the store workers under a team group membership are assigned one of two user roles: "owner" or "member." A store employee with the "owner" user role, typically a store manager, can perform operations such as adding a private channel and adding or deleting members. 

The following image shows an example list of team members and their user roles in Microsoft Teams.

![Dynamics 365 Commerce and Teams integration - User Roles](media/d365-commerce-teams-integration-user-roles.png)

For more information, see [Assign team owners and members in Microsoft Teams](https://docs.microsoft.com/microsoftteams/assign-roles-permissions).

## FAQ

#### How do you assign the "owner" role to a user while provisioning Microsoft Teams from Dynamics 365 Commerce? 

All store managers are added as owners to the corresponding team group so that they can perform operations such as adding a private channel and adding or deleting members. 

#### What happens if a store doesn't have store managers?

If a store doesn't have managers, a team group will not created for the store or in Teams. 

#### What happens if store managers leave the company?

Someone with the "owner" role can add a new store manager in Commerce headquarters and reprovision Teams so that the new manager will have the necessary privileges in Teams for the group. 

#### How do you clear the Microsoft Graph API token stored in the session storage?

A user who has signed in to point of sale (POS) with an Azure Active Directory (Azure AD) account should sign out from the POS or close the application to clear the session storage. 

## Additional resources

[Dynamics 365 Commerce and Microsoft Teams integration ](commerce-teams-integration.md)

[Provision Microsoft Teams from Dynamics 365 Commerce](provision-teams-from-commerce.md)

[Synchronize task management between Microsoft Teams and POS](synchronize-tasks-teams-pos.md)

[Configure Microsoft Teams integration](configure-teams-integration.md)
