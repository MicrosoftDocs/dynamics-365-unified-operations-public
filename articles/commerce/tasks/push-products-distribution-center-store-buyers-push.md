--- 
title: Push products from distribution center to store using buyer's push
description: Learn how to create and process a buyer's push to distribute products from one location to one or many stores in Microsoft Dynamics 365 Commerce. 
author: BrianShook
ms.date: 02/11/2026
ms.topic: how-to 
ms.search.form: RetailBuyersPush, InventLocationIdLookup, InventItemIdLookupSimple, RetailReplenishmentTreeLookup   
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: yufeihuang
ms.search.validFrom: 2016-06-30 
ms.custom: 
  - bap-template
---
# Push products from distribution center to store using buyer's push

[!include [banner](../includes/banner.md)]

This article explains how to create and process a buyer's push to distribute products from one location to one or many stores in Microsoft Dynamics 365 Commerce.

The following procedure walks through the steps to create and process a buyer's push to distribute products from one location to one or many stores in Microsoft Dynamics 365 Commerce. You can define multiple configurations and have the system suggest how to distribute the products, or manually enter where the products are distributed to and how much gets distributed to each store.

This procedure doesn't include setup of data that can be used in the buyer's push, such as replenishment rules, organizational hierarchies, and store weights. The procedure uses the USRT demo company.

To create and process a buyer's push, follow these steps.

1. In Commerce headquarters, go to **Buyer's push**.
1. Select **New**.
1. In the **Description** field, type a value.
1. In the **Site** field, enter or select a value.
1. In the **Warehouse** field, enter or select a warehouse that has products with on-hand quantities.
1. Select **Add**.
1. In the list, mark the selected row.
1. In the **Item number** field, enter or select a product.
1. Select **Add**.
1. In the list, mark the selected row.
1. In the **Item number** field, enter or select a variant product. When you enter a variant product, lines are created for each variant.  
1. In the list, mark a row.
1. In the **Pushed quantity** field, type how many of the selected product you want to distribute.
1. In the **Additional quantity to push** field, enter the quantity of the products that have available quantity to distribute.
1. In the **Distribution** field, enter *Location weight*.
    * You can select the other types to use other rules for the distribution.  
1. In the **Replenishment hierarchy** field, select a value.
1. Select **Yes** in the **Respect assortments** field.
1. Select **Calculate quantities** and review the quantities that are added to the rows in the **Warehouse** section.
1. Select **Create order**.
1. Select **Yes**.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
