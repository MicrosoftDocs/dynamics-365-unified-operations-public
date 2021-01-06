---
# required metadata

title: What's new or changed in Dynamics 365 Talent - Core HR (October 8, 2018)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent - Core HR.
author: Darinkramer
manager: AnnBe
ms.date: 10/07/2018
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
ms.search.validFrom: 2018-10-07
ms.dyn365.ops.version: Talent

---

# What's new or changed in Dynamics 365 Talent - Core HR (October 8, 2018)

**Build 8.1.1050.0**

This topic describes features that are either new or changed in Core HR.

## Allow other dates to be used on leave tier basis (Leave Management)

When awarding leave to employees, the award tier basis determines how much time off an employee accrues. Currently, these tiers are based on employee start date and seniority date. In some scenarios, organizations need these tiers to be based on other dates, like anniversary date or original hire date. These dates are already used on the leave plan to determine when accruals happen, the ability for these same dates to be used when an employee is enrolled in a plan have been added to determine the accrual amount. 

## Other changes
Miscellanous fixes have been included in this release.

## Known issue

**Issue:** When adding a new attachment to a worker, the **New** and **Edit** buttons are grayed out. **Workaround:** Before opening the attachment page, make sure that the FactBoxes on the **Worker** page are closed. If the FactBoxes are closed when the **Worker** page is loaded, the attachments buttons will be enabled. (This issue will be fixed in the next platform update.)
