---
# required metadata
title: [Dynamics 365 Commerce and Microsoft Teams integration - User roles ]
description: [In a better together strategy, Dynamics 365 Commerce is integrating with Microsoft Teams to help customers (C1) and their employees improving productivity by synergize the task management between Dynamics 365 Commerce and Microsoft Teams. This documentation helps you understand different user roles and how to make a store workers as owner of team in Microsoft teams]
author: [gvrmohanreddy]
manager: jeffbl
ms.date: 01/15/2021
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

#Overview

As you create a team per store (or channel) in Microsoft Teams there is a group membership created, for e.g. *HOUSTON_D365@<YourTenantAADDomain>.com* and all the store workers will be assigned with one of two user roles called *owner* and *member*.  Store employee with *owner* user role, typically a Store Manager, can do operations like adding a private channel, adding members etc. 

Refer to Assign team owners and members in Microsoft Teams - Microsoft Teams | Microsoft Docs to learn more. 

![Dynamics 365 Commerce and Teams integration - User Roles](media/d365-commerce-teams-integration-user-roles.png)

##FAQ

How to assign *Owner* role for a user while provisioning Microsoft Teams from Dynamics 365 Commerce? 

All people with Store Managers role will be added as an owner to the corresponding team's group members.  E.g. store managers of Houston will be added as owners to HOUSTON_D365@<TenantAADDomain>.com) so that store managers can perform operations like adding a member of deleting a member from the group as needed. 

What happens if a store doesn't a store managers?
	Group will not created, means not team for the store in the Teams as well. 
What happens if store managers leave the company?
	Add new Store Manager in the HQ and re-provision Teams so that new manager will have required privilege's in the Teams for the group. 
