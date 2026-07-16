---
title: Transfer physical inventory within the warehouse
description: Learn about the process of creating and posting an inventory transfer journal in order to register movement of an item from one location in a warehouse to another.
author: banluo-ms
ms.author: banluo
ms.reviewer: kamaybac
ms.search.form: InventJournalTransfer, InventJournalCreate, InventItemIdLookupSimple, InventLocationIdLookup, WMSLocationIdLookup, InventTrans   
ms.topic: how-to
ms.date: 05/29/2026
ms.custom: 
  - bap-template
---

# Transfer physical inventory within the warehouse

[!include [banner](../../includes/banner.md)]

This procedure shows how to create and post an inventory transfer journal to register movement of an item from one location in a warehouse to another. Before you start, set up an inventory journal name for inventory transfers. You can follow this procedure in the [demo data](../../../fin-ops-core/dev-itpro/get-started/demo-data.md) company USMF using the example values that are shown, or you can use your own data if you have products and locations set up. A warehouse employee normally carries out these tasks.

## Create an inventory transfer journal

1. Go to **Inventory management** > **Journal entries** > **Items** > **Transfer**.
1. On the Action Pane, select **New**.
1. In the **Name** field, enter or select a value.
1. Select **OK**.

## Create journal lines

You can specify *From* and *To* dimensions for each journal line. These dimensions are essential for this journal type. You can transfer items to locations by using different rules. In this example, you transfer an item within the same warehouse, from a license plate controlled location to a location that isn't license plate controlled.

1. On the **Journal lines** FastTab, select **New**.
1. In the **Item number** field, enter or select a value. If you're using USMF, select *A0001*.  
1. In the **From site** field, enter or select a value. If you're using USMF, select *2*.  
1. In the **To site** field, enter or select a value. If you're using USMF, select *2*.  
1. In the **From warehouse** field, enter or select a value. If you're using USMF, select *24*.  
1. In the **To warehouse** field, enter or select a value. If you're using USMF, select *24*.  
1. In the **From location** field, enter or select a value. If you're using USMF, select *FL-001*.  
1. In the **To location** field, enter or select a value. If you're using USMF, select *BULK-001*.  
1. In the **Quantity** field, enter a number.
1. On the **Line details** FastTab, select the **Inventory dimensions** tab.
1. In **From inventory dimensions**, in the **License plate** field, enter or select a value. If you're using USMF, select *24*.  
1. Select **Save**.

## Post the inventory transfer journal

1. On the Action Pane, select **Post**.
1. Select **OK**.

## View inventory transactions

To see the transactions that were created when you posted your journal, follow these steps:

1. On the **Journal lines** FastTab, select the line you want to inspect.
1. On the **Journal lines** FastTab toolbar, select **Inventory** \>  **Transactions**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
