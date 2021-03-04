---
# required metadata
title: Dynamics 365 Commerce and Microsoft Teams integration
description: This topic presents an overview of Microsoft Dynamics 365 Commerce and Microsoft Teams integration.
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

# Dynamics 365 Commerce and Microsoft Teams integration 

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic presents an overview of Microsoft Dynamics 365 Commerce and Microsoft Teams integration.

Dynamics 365 Commerce is integrating with Microsoft Teams to help customers and their employees improve productivity by synchronizing task management between Dynamics 365 Commerce and Microsoft Teams. With Commerce and Teams integration, seamless task management enables store managers and employees to create task lists, assign tasks to multiple stores, and track task status across stores from either application. Commerce and Teams integration is available as of the Commerce version 10.0.18 release.

## Key features 

Key features offered with Commerce and Teams integration include capabilities to:

- Provision Microsoft Teams by leveraging well-defined Commerce organizational structure, stores, workers, permissions, and business context. 
- Easily synchronize ongoing changes such as adding a new store or hiring a new employee between Commerce and Teams, while keeping Commerce as the master source of organizational structure data.  
- Integrate task management between Commerce and Teams to help store workers, store managers, regional managers, and communications managers handle task management from within either application.  

## Prerequisites to using integration features

The following prerequisites are required before you can start using Teams integration features:

- Microsoft 365 Business Standard License (which includes Microsoft Teams).
- Azure Active Directory (Azure AD) accounts for all store managers and workers.
- Point of sale (POS) systems that are configured with Azure AD authentication. 

## Conceptual architecture 

The following illustration shows the conceptual architecture of Commerce and Teams integration.

![Dynamics 365 Commerce - Teams integration](media/d365-commerce-teams-integration-conceptual-architecture.png)

## Additional resources

[Provision Microsoft Teams from Dynamics 365 Commerce](provision-teams-from-commerce.md)

[Synchronize task management between Microsoft Teams and POS](synchronize-tasks-teams-pos.md)

[Configure Microsoft Teams integration](configure-teams-integration.md)

[Manage user roles in Microsoft Teams](manage-user-roles-teams.md)
