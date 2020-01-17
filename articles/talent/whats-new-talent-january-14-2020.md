---
# required metadata

title: What's new or changed in Dynamics 365 Talent (January 14, 2020)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent.
author: Darinkramer
manager: AnnBe
ms.date: 1/14/2020
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
ms.search.validFrom: 2020-01-14
ms.dyn365.ops.version: Talent

---
# "What's new or changed in Dynamics 365 Talent (January 14, 2020)"

[!include [banner](includes/banner.md)]

This topic describes features that are either new or changed in Dynamics 365 Talent.

## Changes in Attract
This release includes minor bug fixes for Dynamics 365 Talent: Attract.

## Changes in Onboard
This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

## Changes in Core HR
Changes described in this section apply to build number 8.1.2709.

### System unable to generate calendar days when importing through Data Management Framework - (381195)

This change corrects an issue where an error message is displayed during the importing of calendar days, "Invalid date format". Work calendar date lines were not created as a result.

## Coming soon

A new CDS solution will be available soon with the following changes.
The Job/Position entity in CDS has the following changes:
    - Compensation region has been added
    - Financial dimensions have been added

The Worker entity in CDS has the following changes:
    - Name sequence has been added
    - Works from home has been added
    - Language has been added
    - Seniority date has been added
    - Anniversary date has been added
    - Original hire date has been added

Employment entity in CDS has the following changes:
    - Financial dimensions have been added
    - Termination reason has been added
    - Termination date ahs been renamed
    - Probation date has been added

Worker address changes in CDS:
    - Street address has been added to the Worker address entity and address lines 1,2,3 have been marked for deprecation.

Variable compensation set up entities included in new solution
    - Compensation variable plan type
    - Compensation variable plan
    - Vesting rules
    - Compensation variable plan level

Worker Calender Employment entity new to CDS:
    - Work calendar entity has been added
