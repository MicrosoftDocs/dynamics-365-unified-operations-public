---
title: Count inventory in a warehouse
description: Learn about the process of creating and posting an inventory counting journal in order to count a specific item at a location in the warehouse.
author: banluo-ms
ms.author: banluo
ms.reviewer: kamaybac
ms.search.form: InventJournalCount, InventJournalCreate, HcmWorkerLookUp, InventItemIdLookupSimple, InventLocationIdLookup, WMSLocationIdLookup, InventTrans
ms.topic: how-to
ms.date: 5/20/2026
ms.custom: 
  - bap-template
---

# Count inventory in a warehouse

[!include [banner](../../includes/banner.md)]

This article describes the process of creating and posting an inventory counting journal to count a specific item at a location in the warehouse. The procedure applies to the Inventory management module when you're not using warehouse management processes (WMS). The procedure doesn't apply to WMS-enabled warehouse functionality that's available in the Warehouse management module. You can walk through this procedure in the [demo data](../../../fin-ops-core/dev-itpro/get-started/demo-data.md) company USMF, or use your own data. If you use your own data, make sure that you set up products and locations, and create an inventory journal name for counting journals. A warehouse employee normally performs inventory counting.

## Create an inventory counting journal

1. Go to **Inventory management** > **Journal entries** > **Item counting** > **Counting**.
1. Select **New**.
1. In the **Name** field, select the inventory counting journal name you want to use from the drop-down list. Some other fields are populated based on the setup of the inventory counting journal name that you select.  
1. In the **Worker** field, select the drop-down button to open the lookup.
1. In the list, **Select** the worker you want to use.
1. Select **OK**.

## Create journal lines

1. Select **New**.
1. In the **Item number** field, select the desired record from the drop-down list. If you're using demo data company USMF, select *A0001*.  
1. In the **Site** field, select the desired record from the drop-down list. If you're using demo data company USMF, select site *2*.
1. In the **Warehouse** field, select the desired record from the drop-down list. If you're using demo data company USMF, select warehouse *24*.  
1. In the **Location** field, select the desired record from the drop-down list. If you're using demo data company USMF, select location *BULK-001*.  
1. In the **Counted** field, enter a number. If you enter a counted number that's different from the number shown in the **On-hand** field, the **Quantity** field is updated to show the discrepancy.    
1. Select **Save**.

## Post the inventory counting journal

1. Select **Post**. When you post an inventory counting journal, if the counted amount differs from the amount that's reported in the **On-hand** field, an inventory receipt or issue is posted. The inventory level and value change, and ledger transactions are generated.
1. Select **OK**.

## View inventory transactions

1. Select **Inventory**.
1. Select **Transactions**. You can see related transactions that are created when you post your inventory counting journal.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
