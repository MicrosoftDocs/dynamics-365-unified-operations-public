--- 
# required metadata 
 
title: Calculate a BOM by using a single level structure (February 2016)
description: This procedure shows how to calculate the cost of a finished product by using single level explosion that is based in the Costing sheet. 
author: JennySong-SH
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: EcoResProductDetailsExtended, InventItemPrice, BOMCalcDialog   
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
# Calculate a BOM by using a single level structure (February 2016)

[!include [banner](../../includes/banner.md)]

This procedure shows how to calculate the cost of a finished product by using single level explosion that is based in the Costing sheet. This is the sixth task in the BOM calculation series. The demo data company used to create this task is USMF.

1. Go to Released products.
2. In the list, find and select the desired record.
    * Select product BOM_1.  
3. On the Action Pane, click Manage costs.
4. Click Item price.
5. Click Calculate item cost.
    * You may need to click the ellipsis (...) to see this option in the top menu.  
6. In the Costing version field, click the drop-down button to open the lookup.
    * For this demo, select 10. This is the same costing version used for adding the cost price to the components.  
7. Click OK.
8. Click View calculation details.
    * You may need to click the ellipsis (...) to see this option in the top menu.    Here's the composition of the cost:  *    10 is derived from ITEM_A, 10 from ITEM_B, 10 from BOM_2. In this case there are no details for BOM_2 because it was entered as a standard cost of 10 but not done through calculation.  *    7 is derived from the setup time, which is a constant cost, and additional 7 is derived from the run-time operation (Process).  *    There are also other amounts that correspond to indirect costs.  
9. @SysTaskRecorder:_RequestClose



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]