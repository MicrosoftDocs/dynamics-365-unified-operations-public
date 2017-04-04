---
# required metadata

title: Bonus depreciation
description: This article provides an overview of the bonus depreciation functionality.
author: twheeloc
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: AssetBonus
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 3621
ms.assetid: 835ec594-744e-461c-a676-1b9abc094173
ms.search.region: Global
# ms.search.industry: 
ms.author: saraschi
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Bonus depreciation

This article provides an overview of the bonus depreciation functionality.

For bonus depreciation, you can take extra or bonus depreciation amounts during the first year that the asset is put in service and depreciated. Bonus depreciation must be taken before any other depreciation calculations. Therefore, it's best to use bonus depreciation with books where the Post to general ledger functionality is disabled. You can use the **Delete transactions not posted to general ledger** option to delete historical transactions for books that don't post to the general ledger. You can then accommodate bonus depreciation later in the asset life cycle by deleting depreciation transactions that were previously posted. 

You can calculate bonus depreciation by using the proposal process, or you can create manual bonus depreciation transactions. You can't create bonus depreciation transactions if depreciation transactions or depreciation adjustment transactions exist for that asset book.

When you use the proposal process to calculate bonus depreciation, all existing bonus transactions are included in the calculation of the basis. The calculation also includes any previous bonus depreciations that you manually entered for the asset. 

If more than one bonus depreciation will be taken for an asset, the priority is considered. Each bonus reduces the asset basis for the next bonus. Salvage value isn't considered in the asset basis for bonus depreciation calculations, and the depreciation convention doesn't apply for bonus depreciation. 

Currently, in the United States, some property qualifies as Section 179 property. By using the Section 179 deduction, you can recover all or part of the cost of some property, up to a limit. You can recover the cost by deducting it in the year when you put the property in service.

## Example
The following bonus depreciations are associated with an asset book:

-   **Section 179:** 1,000.00, Priority 1
-   **Liberty Zone:** 30 percent, Priority 2

The asset acquisition cost is 5,000.00. When bonus depreciation is calculated, the first bonus depreciation amount is 1,000.00 for the Section 179 depreciation. 

The next bonus depreciation amount, for the Liberty Zone depreciation, is calculated as follows: 

Acquisition cost – 1,000 (Section 179 depreciation) × 30 percent = 1,200 

If the bonus depreciation amount is more than the remaining acquisition cost, the bonus depreciation amount is either the result of the bonus depreciation calculation or the remaining acquisition cost, whichever amount is less. 

If the remaining acquisition cost is 0 (zero) or less, bonus depreciation transactions isn't generated. 

When bonus depreciation is calculated by using the proposal process, a bonus depreciation transaction is created for all applicable bonus depreciation records that are associated with the asset book. 

You can create an unlimited number of bonus depreciation records. After you assign those records to the asset group book, they are applied to the asset book. 

Bonus depreciation is entered as either a percentage or a fixed amount. When you post depreciation proposals, bonus depreciation transactions are posted to the book as separate transactions from the depreciation transactions.

