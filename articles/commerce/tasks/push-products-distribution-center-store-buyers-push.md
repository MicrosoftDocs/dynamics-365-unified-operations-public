--- 
# required metadata 
 
title: Push products from distribution center to store using buyer's push
description: This procedure walks through the steps to create and process a Buyer´s push to distribute products from one location to one or many stores. 
author: BrianShook
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: RetailBuyersPush, InventLocationIdLookup, InventItemIdLookupSimple, RetailReplenishmentTreeLookup   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Retail
ms.author: brshoo
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Push products from distribution center to store using buyer's push

[!include [banner](../includes/banner.md)]

This procedure walks through the steps to create and process a Buyer´s push to distribute products from one location to one or many stores. The user can define multiple configurations and have the system suggest how to distribute the products, or manually enter where the products are distributed to and how much gets distributed to each store. This procedure doesn't include setup of data that can be used in the Buyer´s push, such as replenishment rules, organizational hierarchies, and store weights. This procedure uses the USRT demo company.

1. Go to Buyer's push.
2. Click New.
3. In the Description field, type a value.
4. In the Site field, enter or select a value.
5. In the Warehouse field, enter or select a warehouse that has products with on-hand quantities.
6. Click Add.
7. In the list, mark the selected row.
8. In the Item number field, enter or select a product.
9. Click Add.
10. In the list, mark the selected row.
11. In the Item number field, enter or select a variant product.
    * When entering a variant product, lines will be created for each variant.  
12. In the list, mark a row.
13. In the Pushed quantity field, type how many of the selected product you want to distribute.
14. In the Additional quantity to push field, enter the quantity of the products that have available quantity to distribute.
15. In the Distribution field, enter 'Location weight'.
    * You can select the other types to use other rules for the distribution.  
16. In the Replenishment hierarchy field, select a value.
17. Select Yes in the Respect assortments field.
18. Click Calculate quantities and review the quantities that are added to the rows in the Warehouse section.
19. Click Create order.
20. Click Yes.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]