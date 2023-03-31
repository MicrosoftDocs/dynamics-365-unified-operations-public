--- 
# required metadata 
 
title: Set up accessorial assignments
description: This procedure shows how to set up an accessorial assignment. 
author: Weijiesa
ms.date: 11/14/2016
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: TMSAccessorialAssignment
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: weijiesa
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Set up accessorial assignments

[!include [banner](../../includes/banner.md)]

This procedure shows how to set up an accessorial assignment. This is typically done by a transportation coordinator. Before you use this guide you need to run the "Set up hub accessorial charges and accessorial masters" guide.


## Set up Accessorial assignment
1. Go to Transportation management > Setup > Rating > Accessorial assignments.
2. Click New.
3. In the Name field, type a value.
4. Toggle the expansion of the Details section.
5. In the Hub field, click the drop-down button to open the lookup.
6. In the list, select the Hub that you created an accessorial master for when you ran the "Set up hub accessorial charges and accessorial masters" guide. 
7. In the Hub accessorial ID field, click the drop-down button to open the lookup.
8. In the list, click the link in the selected row.
9. Toggle the expansion of the Criteria section.
    * In the Criteria section you can choose the exact criteria for when the charge should apply, based on the different values offered here.  
10. Set the Always apply option to Yes.
11. In the Accessorial assignment level field, select an option.
12. Toggle the expansion of the Calculation section.
13. In the Accessorial fee type field, select 'Flat'.
    * The Accessorial fee type determines how to calculate the actual charge. In this example it's a flat charge.  
14. In the Accessorial fee field, enter a number.
15. Click Save.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]