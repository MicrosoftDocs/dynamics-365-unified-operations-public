---
# required metadata

title: What's new or changed in Dynamics 365 Talent - Core HR (September 24, 2018)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent - Core HR.
author: Darinkramer
manager: AnnBe
ms.date: 09/21/2018
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
ms.search.validFrom: 2018-09-30
ms.dyn365.ops.version: Talent

---
# What's new or changed in Dynamics 365 Talent - Core HR (September 24, 2018)

**Build 8.1.1015.0**

This topic describes features that are either new or changed in Core HR.

## Currency added to Benefits

Benefit plans have been updated to include the currency of the benefit. This new
field is also available on worker enrolled benefits. 
This new field is part of the Maintain benefits and View a list of benefits security privilege.

## Update proration process – Leave and Absence

Organizations award time off differently based on when employees join and leave
the company. For employees leaving the organization, some may need to end the
award on the termination date, while others rely on the last day worked to stop
the accrual process. These changes provide organizations the ability to choose
when to end enrollment during the termination process. 
These new options are part of the privileges for Terminate a worker and Terminate a worker from manager self service. 

## Other changes

This release includes several additional bug fixes.

## Known Issue

-   **Issue:** When adding a new attachment to a worker, the **New** and **Edit** buttons are grayed out. **Workaround:** Before opening the attachment page, make sure that the fact
    boxes on the **Worker** page are closed. If the fact boxes are closed when the **Worker** page is loaded, the attachments buttons will be enabled. (This issue will be fixed in the next platform update.)
