---
# required metadata

title: What's new or changed in Dynamics 365 Talent (February 14, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent.
author: Darinkramer
manager: AnnBe
ms.date: 02/14/2019
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
# ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2019-02-14
ms.dyn365.ops.version: Talent

---
# What's new or changed in Dynamics 365 Talent (February 14, 2019)

This topic describes features that are either new or changed in Talent.

## Changes in Attract
There are minor bug fixes included with this release.

## Changes in Onboarding
There are minor bug fixes included with this release.
 
## Changes in Core HR 
**Build 8.1.2146**

### Employee fixed compensation entity doesn't export all records
With this change, the **Employee fixed compensation** entity will now export all records. The entity can be used to create and update existing fixed compensation records for employees. 

### Employment end date doesn't honor employee preferred time zone settings
Employment end dates are now honoring the user-preferred time zone when creating or ending employment with a company.
 
### UK addresses display in Analytics as Eastern Switzerland addresses
In this release, a change has been made to correct misalignment in addresses in the **Personnel Management** "Headcount by location" report.
 
### Termination code is not populated on the worker position assignment record when ending the position
A change has been made to default the "Termination reason" code when ending the employees position assignment.

### New entity created for job compensation levels
A new data management framework (DMF) entity was created. The entity provides for creation and updates to compensation levels, market values, and survey information for each job defined in the system.
