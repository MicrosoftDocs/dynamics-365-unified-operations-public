---
title: Correct inventory tracking information
description: Learn about the process of creating and posting an inventory transfer journal in order to correct inventory tracking information.
author: banluo-ms
ms.author: banluo
ms.reviewer: kamaybac
ms.search.form: InventJournalTransfer, InventJournalCreate, InventItemIdLookupSimple, InventBatchIdLookup, InventLocationIdLookup, InventDimTracking, InventTrans  
ms.topic: how-to
ms.date: 11/12/2025
ms.custom:
  - bap-template
---

# Correct inventory tracking information

[!include [banner](../../includes/banner.md)]

This procedure walks you through the process of creating and posting an inventory transfer journal to correct inventory tracking information. In this example, you update the information of a batch-controlled item by changing an incorrectly registered batch to another batch. You can walk through this procedure in demo data company *USPI*, or use your own data. If you use your own data, you need to have an item that's batch-enabled, and it must not be location-controlled. You also need to have an inventory journal name set up for inventory transfers. These tasks are normally carried out by a warehouse employee.

## Create an inventory transfer journal

To create an inventory transfer journal, follow these steps:

1. Go to **Transfer**.
1. Select **New**.
1. In the **Name** field, enter or select a value.
1. Select **OK**.

## Create journal lines

To create journal lines, follow these steps:

1. Select **New**.
1. In the **Item number** field, enter or select a value. If you're using *USPI* demo data, select item *M5003*.  
1. In the **Quantity** field, enter a number.
1. Select the **Inventory dimensions** tab.
1. In the **Batch number** field, enter or select a value.
1. In the **Site** field, enter or select a value.
1. In the **Warehouse** field, enter or select a value.
1. In the **Batch number** field, enter or select a value.

## Post the journal

To post the journal, follow these steps:

1. Select **Post**.
1. Select **OK**.

## Check tracing information

To check tracing information, follow these steps:

1. Select **Inventory**.
1. Select **Trace**.
1. Select **OK**. With this tracing information, you can trace back to the batch you corrected inventory from. You can also use the Item tracing page to see this information.  
1. Close the page.

## Check inventory transactions

To check inventory transactions, follow these steps:

1. Select **Inventory**.
1. Select **Transactions**. Here you can see the transactions that were created when you posted your journal.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
