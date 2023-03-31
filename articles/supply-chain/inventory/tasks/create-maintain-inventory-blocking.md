--- 
# required metadata 
 
title: Create and maintain an inventory blocking
description: This article describes how to use an inventory blocking to prevent physical on-hand inventory from being reserved by other outbound source documents.
author: yufeihuang
ms.date: 03/23/2021
ms.topic: how-to 
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
ms.author: yufeihuang
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---

# Create and maintain an inventory blocking

[!include [banner](../../includes/banner.md)]

This article describes how to use an inventory blocking to prevent physical on-hand inventory from being reserved by other outbound source documents. Before you start the procedures in this article, you must have an item that physical on-hand inventory is available for.

## Block inventory

To create an inventory blocking record so that inventory is blocked, follow these steps.

1. Go to **Inventory management \> Periodic tasks \> Inventory blocking**.
1. On the Action Pane, select **New**.
1. On the header of the new blocking record, set the **Item number** field to the item that you want to block, and enter a description.
1. On the **General** FastTab, in the **Quantity** field, enter the number of items to block.
1. On the **Inventory dimensions** FastTab, specify the site and warehouse where the items that you want to block are currently located.
1. On the Action Pane, select **Save**.

## Update the conditions of the inventory blocking

To update an inventory blocking record, follow these steps.

1. Go to **Inventory management \> Periodic tasks \> Inventory blocking**.
1. In the list pane, select the relevant blocking record.
1. Edit the record as required. For example, you might change the value of the **Expected date** field to indicate when the blocked inventory is expected to become available for reservation. If the **Expected receipts** option is selected, the date will appear on the expected transaction. (The **Expected receipts** option is selected by default when you manually create a blocking record.)
1. On the Action Pane, select **Save**.

## Unblock inventory

To remove an inventory blocking record so that inventory is unblocked, follow these steps.

1. Go to **Inventory management \> Periodic tasks \> Inventory blocking**.
1. In the list pane, select the relevant blocking record.
1. On the Action Pane, select **Delete**.
1. You're prompted to confirm the operation. Select **Yes** to continue.
1. Close the page.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
