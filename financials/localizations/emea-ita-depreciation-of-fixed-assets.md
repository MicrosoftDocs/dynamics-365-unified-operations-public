---
# required metadata

title: Manual depreciation of fixed assets for Italy
description: This topic provides information about fixed assets depreciation for legal entities in Italy. 
author: ShylaThompson
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: AssetDepreciationProfile, LedgerJournalTransApprove, LedgerJournalTransAsset, LedgerJournalTransDaily, LedgerJournalTransVendInvoice, PurchTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 81
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 264294
ms.assetid: 89d8fca3-b653-4fc8-9186-b765c31f7544
ms.search.region: Italy
# ms.search.industry: 
ms.author: v-elgolu
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1

---

# Manual depreciation of fixed assets for Italy

[!include[banner](../includes/banner.md)]


This topic provides information about fixed assets depreciation for legal entities in Italy. 

For legal entities in Italy, the manual depreciation method has additional functionality that includes the following fields:

-   **Calculation basis** -** **This field has two options: **Days** or **Months** on the **Depreciation profiles** page. Fixed assets depreciation is calculated for the year as follows:
    -   Days depreciation = Full years depreciation \* (number of days remaining/total days in the year)
    -   Months depreciation = Full years depreciation \* (number of months remaining/12)
-   **Depreciation run date** - This field was added to the following pages:
    -   General journal
    -   Fixed asset journal
    -   Invoice approval journal
    -   Invoice journal
    -   Purchase order

The **Depreciation run date** should be set up at the time of acquisition and is set to the system date during the acquisition. The **Depreciation run date** is used to calculate depreciation for the **Number of days remaining** or **Number of Months remaining**, depending on the **Calculation basis** value. If the **Depreciation run date** is before the middle of the month (either the 15th or 14th for February), then the current month is included in number of months, otherwise the asset is considered as acquired in the next month.



