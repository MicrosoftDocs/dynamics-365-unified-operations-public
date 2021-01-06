---
# required metadata

title: What's new or changed in Dynamics 365 Talent - Core HR (October 15, 2018)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent - Core HR.
author: Darinkramer
manager: AnnBe
ms.date: 10/15/2018
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
ms.search.validFrom: 2018-10-11
ms.dyn365.ops.version: Talent

---
# What's new or changed in Dynamics 365 Talent - Core HR (October 15, 2018)

**Build 8.1.1056**

This topic describes features that are either new or changed in Core HR.


## Changes
In addition to miscellanous fixes, the following updates have been made in this release:
- Last Day worked now set when hiring or setting an employment end date.
- US compliance references removed when in non US companies (ACA, ADA, and I9).
- Invalid dates (1/1/1900) are now hidden on analytics pages.

## Known issue

**Issue:** When adding a new attachment to a worker, the **New** and **Edit** buttons are grayed out. **Workaround:** Before opening the attachment page, make sure that the FactBoxes on the **Worker** page are closed. If the FactBoxes are closed when the **Worker** page is loaded, the attachments buttons will be enabled. (This issue will be fixed in the next platform update.)
