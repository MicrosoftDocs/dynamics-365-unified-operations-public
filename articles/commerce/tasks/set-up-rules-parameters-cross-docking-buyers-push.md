--- 
# required metadata 
 
title: Set up rules and parameters for cross docking and buyer's push
description: This procedure demonstrates the steps to create Replenishment rules. 
author: josaw1
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: RetailReplenishmentRuleTable, RetailReplenishmentTreeLookup   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Set up rules and parameters for cross docking and buyer's push

[!include [banner](../includes/banner.md)]

This procedure demonstrates the steps to create Replenishment rules. Replenishment rules can be used to control how products are distributed to stores when using Cross-docking and Buyer´s push. Replenishment rules can be set up for stores or store groups. The weight defined for each line in a rule will control how the quantities of products will get distributed between the stores when using Replenishment rules as the distribution method in Cross-docking or Buyer´s push. This procedure uses the USRT demo company.

1. Go to Replenishment rules.
2. Click New.
3. In the Replenishment rule field, type a value.
4. In the Description field, type a value.
5. Click Save.
6. Click Add.
7. In the list, mark the selected row.
    * You can choose Replenishment hierarchy or Channel for the type. The value controls whether the selection in Name will be a hierarchy of channels or a specific channel.  For this example, leave it set as Replenishment hierarchy.  
8. In the Name field, select a value.
    * The default weight value is populated from the weight defined on the warehouse.  This weight can be used for the Replenishment rule or you can enter a new weight in the Weight field.  
9. In the Weight field, enter a number.
10. Click Add.
11. In the list, mark the selected row.
12. In the Type field, select 'Channel'.
13. In the Name field, enter or select a value.
14. In the Weight field, enter a number.
15. Click Save.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]