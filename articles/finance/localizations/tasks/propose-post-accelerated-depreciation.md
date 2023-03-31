---
title: Propose and post accelerated depreciation
description: For Japan, you can propose an accelerated depreciation based on the data on confirmed accelerated depreciation documents.
author: kfend
ms.date: 08/29/2018
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Japan
ms.author: kfend
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: LedgerJournalTable, LedgerJournalTransAsset, AssetAcceleratedDepDocument_JP
---
# Propose and post accelerated depreciation

[!include [banner](../../includes/banner.md)]

For Japan, you can propose an accelerated depreciation based on the data on confirmed accelerated depreciation documents. Note: The accelerated depreciation proposal will not propose ordinary depreciation. This procedure must be completed after you post ordinary depreciation.



This procedure walks you through proposing and posting an accelerated depreciation document based on confirmed accelerated depreciation documents. 



In order to complete this procedure, the Fixed asset configuration key must be selected.



This procedure was created using the demo data company JPMF.

1. Go to Fixed assets > Journal entries > Fixed assets journal.
2. Click New.
3. In the Name field, type a value.
4. Click Save.
5. Click Lines.
6. Click Proposals.
7. Click Accelerated depreciation proposal.
8. In the To date field, enter a date.
    * By default, the criteria is configured to propose all confirmed accelerated depreciation documents. You can change this if there is any other needs such as proposing for one specific document.  
9. Click OK.
    * Confirm that the accelerated depreciation was proposed.  
    * Note: The ordinary depreciation is not handled, and therefore, still needs user's operation to propose and post it.  
10. Click Post.
11. Close the page.
12. Go to Fixed assets > Periodic tasks > Accelerated depreciation > Accelerated depreciation document.
    * Confirm that the status of posted document has been updated.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
