---
title: Adjustment of the asset retirement obligation estimate
description: For Japan, the initial estimate of the asset retirement obligations (ARO) can be adjusted.
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
ms.search.form: AssetTable, AssetRetirementObligation_JP, AssetRetirementObligationLine_JP, LedgerJournalTable, LedgerJournalTransAsset, SysQueryForm
---
# Adjustment of the asset retirement obligation estimate

[!include [banner](../../includes/banner.md)]

For Japan, the initial estimate of the asset retirement obligations (ARO) can be adjusted. 



Use this procedure to learn how to adjust the ARO amount.



To complete this procedure, the Fixed Assets configuration key must be selected.



This task was created using the demo data company JPMF.


## Adjust the ARO estimate
1. Go to Fixed assets > Asset retirement obligations > Fixed assets.
2. In the list, find and select the desired record.
3. On the Action Pane, click Fixed asset.
4. Click Asset retirement obligation.
5. Click Upward to open the drop dialog.
    * You can also click Downward for minus adjustment.  
6. In the Transaction date field, enter the date on which to post the adjustment amount.
7. In the Upward field, enter the amount of adjustment.
8. Click OK.

## Post the adjustment
1. Go to Fixed assets > Asset retirement obligations > Fixed assets journal.
2. Click New.
3. In the Name field, type a value.
4. Click Save.
5. Click Lines.
6. Click Proposals.
7. Click Capitalized asset retirement obligation.
8. In the To date field, enter a date.
9. Click Filter.
10. In the Criteria field, type a value.
11. Click OK.
12. Click OK.
    * Confirm the adjustment is proposed. The amount proposed is discounted to the present value.  
13. Click Post.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
