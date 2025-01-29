---
title: Transfer physical inventory within the warehouse
description: Learn about the process of creating and posting an inventory transfer journal in order to register movement of an item from one location in a warehouse to another.
author: Weijiesa
ms.author: weijiesa
ms.reviewer: kamaybac
ms.search.form: InventJournalTransfer, InventJournalCreate, InventItemIdLookupSimple, InventLocationIdLookup, WMSLocationIdLookup, InventTrans   
ms.topic: how-to
ms.date: 11/19/2024
ms.custom: 
  - bap-template
---

# Transfer physical inventory within the warehouse

[!include [banner](../../includes/banner.md)]

This procedure walks you through the process of creating and posting an inventory transfer journal in order to register movement of an item from one location in a warehouse to another. You need to have an inventory journal name set up for inventory transfers before you start this. You can walk through this procedure in [demo data](../../../fin-ops-core/dev-itpro/get-started/demo-data.md) company USMF using the example values that are shown, or using you can use your own data if you have products and locations set up. These tasks would normally be carried out by a warehouse employee.

## Create an inventory transfer journal

1. Go to **Inventory management > Journal entries > Items > Transfer**.
2. On the Action Pane, select **New**.
3. In the **Name** field, enter or select a value.
4. Select **OK**.

## Create journal lines

There are options to specify *From* and *To* dimensions for each journal line. These are essential for this journal type. You can transfer items to locations using different rules. In this example we'll transfer an item within the same warehouse, from a license plate controlled location to a location that is not license plate controlled.

1. On the **Journal lines** FastTab, select **New**.
2. In the **Item number** field, enter or select a value. If you are using USMF, you can select *A0001*.  
3. In the **From site** field, enter or select a value. If you are using USMF, you can select *2*.  
4. In the **To site** field, enter or select a value. If you are using USMF, you can select *2*.  
5. In the **From warehouse** field, enter or select a value. If you are using USMF, you can select *24*.  
6. In the **To warehouse** field, enter or select a value. If you are using USMF, you can select *24*.  
7. In the **From location** field, enter or select a value. If you are using USMF, you can select *FL-001*.  
8. In the **To location** field, enter or select a value. If you are using USMF, you can select *BULK-001*.  
9. In the **Quantity** field, enter a number.
10. On the **Line details** FastTab, select the **Inventory dimensions** tab.
11. In **From inventory dimensions**, in the **License plate** field, enter or select a value. If you are using USMF, you can select *24*.  
12. Select **Save**.

## Post the inventory transfer journal

1. On the Action Pane, select **Post**.
2. Select **OK**.

## View inventory transactions

To see the transactions that were created when you posted your journal, follow these steps.

1. On the **Journal lines** FastTab, select the line you want to inspect.
1. On the **Journal lines** FastTab toolbar, select **Inventory** \>  **Transactions**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
