--- 
# required metadata 
 
title: Count inventory in a warehouse
description: This article describes the process of creating and posting an inventory counting journal in order to count a specific item at a location in the warehouse. 
author: yufeihuang
ms.date: 07/09/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: InventJournalCount, InventJournalCreate, HcmWorkerLookUp, InventItemIdLookupSimple, InventLocationIdLookup, WMSLocationIdLookup, InventTrans   
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
# Count inventory in a warehouse

[!include [banner](../../includes/banner.md)]

This article describes the process of creating and posting an inventory counting journal in order to count a specific item at a location in the warehouse. The procedure applies to "basic warehousing" functionality, available in the Inventory management module, not to the warehousing functionality that's available in the Warehouse management module. You can walk through this procedure in demo data company USMF, or using your own data. If you're using your own data, make sure that you have products and locations set up, and that you've created an inventory journal name for counting journals. Inventory counting is normally carried out by a warehouse employee.


## Create an inventory counting journal
1. Go to **Inventory management > Journal entries > Item counting > Counting**.
2. Select **New**.
3. In the **Name** field, select the inventory counting journal name you want to use from the drop-down list. Some other fields will be populated based on the setup of the inventory counting journal name that you select.  
4. In the **Worker** field, select the drop-down button to open the lookup.
5. In the list, **Select** the worker you want to use.
6. Select **OK**.

## Create journal lines
1. Select **New**.
2. In the **Item number** field, select the desired record from the drop-down list. If you are using demo data company USMF, select **A0001**.  
3. In the **Site** field, select the desired record from the drop-down list. If you are using demo data company USMF, select site **2**.
4. In the **Warehouse** field, select the desired record from the drop-down list. If you are using demo data company USMF, select warehouse **24**.  
5. In the **Location** field, select the desired record from the drop-down list. If you are using demo data company USMF, select location **BULK-001**.  
6. In the Counted field, enter a number. If you enter a counted number that's different to the number shown in the **On-hand** field, the **Quantity** field is updated to show the discrepancy.  
7. Select **Save**.

## Post the inventory counting journal
1. Select **Post**. When you post an inventory counting journal, if the counted amount differs from amount that's reported in the **On-hand** field an inventory receipt or issue is posted, the inventory level and value are changed, and ledger transactions are generated.
2. Select **OK**.

## View inventory transactions
1. Select **Inventory**.
2. Select **Transactions**. Here you can see any related transactions that will be created when you post your inventory counting journal.   



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]