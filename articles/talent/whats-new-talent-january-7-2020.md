---
# required metadata

title: What's new or changed in Dynamics 365 Talent (January 7, 2020)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Talent.
author: Darinkramer
manager: AnnBe
ms.date: 01/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
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
# What's new or changed in Dynamics 365 Talent (January 7, 2020)

This article describes features that are either new or changed in Dynamics 365 Talent.

## Changes in Attract

This release includes minor bug fixes for Dynamics 365 Talent: Attract.

## Changes in Onboard

This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

## Changes in Core HR

Changes described in this section apply to build number 8.1.2697. The numbers in parentheses in some headings refer to support numbers in Microsoft Dynamics Lifecycle Services (LCS).

 
### Can't delete workers that don't have employment records - (386157)

This change adds a delete option in the **Workers without employment** form. Workers appear in this form when no future, active, or historical employments exist for the worker. In this release, delete is only enabled for System Administrators. However, in next week's release, security will be updated to allow all users with the HR assistant role to remove employees without employments. You can also make these changes manually by following the following steps.

1. Go to **Security configuration**.
2. In the **Privileges** tab, filter the **Privileges** list to **Maintain workers**.
3. In the **References** column, select **Display menu items**.
4. In **Display menu items**, select **HcmWOrkersWithoutEmployment**.
5. Set the **Delete** permission to Grant.
6. Select the **Unpublished objects** tab.
7. Select **Publish all**.
