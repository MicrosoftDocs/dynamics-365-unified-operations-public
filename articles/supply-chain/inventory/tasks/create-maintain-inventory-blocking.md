--- 
# required metadata 
 
title: Create and maintain an inventory blocking
description: This procedure shows how to prevent physical on-hand inventory from being reserved by other outbound source documents by using the inventory blocking. 
author: perlynne
manager: tfehr 
ms.date: 03/23/2021
ms.topic: business-process 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: InventBlocking, InventItemIdLookupSimple, InventLocationIdLookup   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: perlynne
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---

# Create and maintain an inventory blocking

[!include [banner](../../includes/banner.md)]

This topic shows how to use inventory blocking to prevent physical on-hand inventory from being reserved by other outbound source documents. You must have an item with physical on-hand inventory available before you start this procedure.

## Block inventory

To create an inventory blocking record, and thereby block inventory:


1. Go to **Inventory management > Periodic tasks > Inventory blocking**.
1. On the Action Pane, select **New**.
1. In the header of the new blocking record, set **Item number** to the item you want to block and add a **Description**.
1. Expand the **General** FastTab and enter the number of items to block in the **Quantity** field.
1. Expand the **Inventory dimensions** fastTab and specify the **Site** and **Warehouse** where the items you want to block are currently located.
1. On the Action Pane, select **Save**.

## Update the conditions of the inventory blocking

To update an inventory blocking record:

1. Go to **Inventory management > Periodic tasks > Inventory blocking**.
1. Select the relevant blocking record from the list pane.
1. Edit the record as needed. For example, you might change the **Expected date** to indicate when the blocked inventory is expected to become available for reservation. If the **Expected receipts** option is selected, as it is by default when you manually create a blocking, this date will appear on the expected transaction.  
1. On the Action Pane, select **Save**.

## Unblock inventory

To remove an inventory blocking record, and thereby unblock inventory:

1. Go to **Inventory management > Periodic tasks > Inventory blocking**.
1. Select the relevant blocking record from the list pane.
1. On the Action Pane, select **Delete**.
1. You are asked to confirm the operation. Select **Yes** to continue.
1. Close the page.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]