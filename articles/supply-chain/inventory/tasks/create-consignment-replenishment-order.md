--- 
# required metadata 
 
title: Create a consignment replenishment order
description: This article explains how to create a consignment replenishment order where you can track the expected delivery from a vendor into your consignment inventory. 
author: yufeihuang
ms.date: 08/19/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: ConsignmentReplenishmentOrder, ConsignmentReplenishmentOrderCreate, InventTrans, ConsignmentDraftReplenishmentOrderJournal, InventOnhandMovement, InventOnhandItem, InventItemIdLookupSimple, ConsignmentProductReceiptJournal, ConsignmentReplenishmentOrderLineQuantity
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: yufeihuang
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create a consignment replenishment order

[!include [banner](../../includes/banner.md)]

This article explains how to create a consignment replenishment order where you can track the expected delivery from a vendor into your consignment inventory. It also shows how to record a receipt of products so that the consignment inventory is registered as on-hand inventory owned by the vendor. This procedure would typically be done by a procurement professional. You can use this guide in demo data company USMF. This procedure is for a feature that was added in Dynamics 365 for Operations, version 1611.

## Create a consignment replenishment order
1. Go to **Procurement and sourcing > Consignment > Consignment replenishment orders**.
2. Select **New**.
3. In the **Vendor account** field, select vendor **US-104** (you must select a vendor that's registered as an owner in the **inventory owners** page). 
4. Select **OK**.
5. Select **Add line**.
6. In the **Item number** field, type `M9211CI` (you must select an item that is set up for consignment inventory).
7. In the **Quantity** field, enter a number.
8. In the **Requested delivery date** field, enter a date. The requested and confirmed dates are used by the MRP engine for the expected arrival of the goods.  
9. In the **Confirmed delivery date** field, enter a date.
10. Expand the **Line details** section.
11. Select the **Inventory dimensions** tab.
12. To show the owner in the **Inventory dimensions owner** field, refresh the page. Vendor US-104 is now listed as the owner.  

## Check the inventory transaction status
1. Select **Inventory**.
2. Select **Transactions**.
3. In the desired row, notice that the **Receipt** field is set to **Ordered**.  
4. Close the page.

## Receive items
1. Select **Product receipt**.
2. In the **External product receipt** field, type a value.
3. In the **Quantity** field, enter a number that's lower than the number that's shown there. 
4. Select **OK**.

## Check the on-hand inventory
1. Select **Inventory**.
2. Select **On-hand**.
3. Select **Overview**. The items that have been received as consignment inventory owned by the vendor are available on-hand. The remaining quantity on the consignment replenishment order is shown in the **Ordered in total** field.  
4. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]