---
# required metadata

title: What's new or changed in Dynamics 365 Talent (January 7, 2020)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent.
author: Darinkramer
manager: AnnBe
ms.date: 1/7/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2020-01-07
ms.dyn365.ops.version: Talent

---
# "What's new or changed in Dynamics 365 Talent (January 7, 2020)"

[!include [banner](includes/banner.md)]

This topic describes features that are either new or changed in Dynamics 365 Talent.

## Changes in Attract
This release includes minor bug fixes for Dynamics 365 Talent: Attract.

## Changes in Onboard
This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

## Changes in Core HR
Changes described in this section apply to build number 8.1.2697.

 
### Can't delete workers that don't have employment records - (386157)

This change adds a delete option in the *Workers without employment* form. Workers will appear in this form when no future, active or historical employments exist for the worker. In this release the delete is only enabled for System Administrators. However, next week's release security will be updated to allow all users with the HR assistant role to remove employments. You can also make these changes manually by following the following steps
1. Go to 'Security configuration'
2. Highlight privileges tab on the top
3. Filter the privileges list to 'Maintain workers'
4. Go to References grid in the middle column and select 'Display menu items'
5. In the 'Display menu items' grid, select the 'HcmWOrkersWithoutEmployment' display menu item
6. Set the 'Delete' permission to Grant.
7. Click the 'Unpublished objects' tab on the top
8. Click the 'Publish all' button
