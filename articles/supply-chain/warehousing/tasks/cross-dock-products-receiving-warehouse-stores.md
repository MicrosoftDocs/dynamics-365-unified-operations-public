--- 
# required metadata 
 
title: Cross-dock products from receiving warehouse to stores
description: This procedure walks through the steps to create and process a Cross-dock to distribute products from the receiving location of a purchase order to one or many stores. 
author: Mirzaab
ms.date: 02/17/2016
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: RetailBuyersPushPerPackage
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: mirzaab
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Cross-dock products from receiving warehouse to stores

[!include [banner](../../includes/banner.md)]

This procedure walks through the steps to create and process a Cross-dock to distribute products from the receiving location of a purchase order to one or many stores. The user can define multiple configurations and have the system suggest how to distribute the products, or manually enter where the products are distributed to and how much gets distributed to each store. The procedure doesn't include setup of data that can be used in the Cross-dock, such as replenishment rules, organizational hierarchies, and store weights. The procedure uses the USRT demo company.

1. Go to All purchase orders.
2. Select a purchase order in the list and click the link to open the order.
3. On the Action Pane, click Retail and Commerce.
4. Click Cross docking.
5. Click Edit.
    * The category can be used to filter the items in the Lines section.  
6. In the list, find and select the desired record.
7. In the Cross docking quantity field, type a value to specify how much of the quantity being purchased of the selected product should be distributed.
8. In the Additional cross docking quantity field, enter a value to specify the quantities to distribute for the available products being purchased
9. In the Distribution field, enter 'Location weight'.
    * You can select the other types to use different rules for the distribution.  
10. In the Replenishment hierarchy field, select a value.
11. Select Yes in the Respect assortments field.
12. Click Calculate quantities.
13. Click Create order.
14. Click Yes.
15. In the list, find and select a warehouse that received products
16. Click Order to view the orders that got created for the selected warehouse



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]