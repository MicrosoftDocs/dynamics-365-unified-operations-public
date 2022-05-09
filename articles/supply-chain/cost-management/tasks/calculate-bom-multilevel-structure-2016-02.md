--- 
# required metadata 
 
title: Calculate a BOM by using a multilevel structure (February 2016)
description: This procedure shows how to calculate the cost of a finished product by using multilevel explosion that is based in the Costing sheet. 
author: JennySong-SH
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: EcoResProductDetailsExtended, InventItemPrice, BOMCalcDialog, BOMCalcTrans   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: yanansong
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Calculate a BOM by using a multilevel structure (February 2016)

[!include [banner](../../includes/banner.md)]

This procedure shows how to calculate the cost of a finished product by using multilevel explosion that is based in the Costing sheet. It is the seventh task in the BOM calculation series. The demo data company used to create this task is USMF.

1. Go to Product information management > Products > Released products.
2. In the list, find and select the desired record.
    * Select product BOM_1.  
3. On the Action Pane, click Manage costs.
4. Click Item price.
5. Click Calculate item cost.
    * You may need to click the ellipsis (...) to see this option in the top menu.  
6. In the Costing version field, enter or select a value.
    * Select Costing version 20, because it's Planned cost type and Explosion mode is Multilevel.   The Multilevel explosion mode is for planned costs and simulations. It is not used for standard cost.  
7. Click OK.
8. Click View calculation details.
    * You may need to click the ellipsis (...) to see this option in the top menu.  In this case, notice how BOM_2 has been calculated taking into account the raw material, process, and overhead with a total of 29,40 instead of the standard cost of 10 that was activated in the initial task guide in this series.  
9. Click the Costing sheet tab.
    * Moving to the Costing sheet tab, the totals per cost group are different compared to the calculation done in previous task guide.  
10. In the Level field, select 'Multi'.
    * When selecting Multi, the costs are classified according to the composition of BOM_2, where 10 is derived from the M1 cost group (ITEM_C), and 15,60 is derived from its manufacturing where the cost group is L2. Indirect costs also vary.  
11. Close the page.
12. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]