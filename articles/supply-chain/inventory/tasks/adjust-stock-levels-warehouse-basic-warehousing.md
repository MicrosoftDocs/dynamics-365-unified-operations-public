--- 
title: Adjust stock levels in the warehouse (basic warehousing)
description: This procedure walks you through the process of creating and posting an inventory adjustment journal in order to adjust stock levels of products in the warehouse.
author: Weijiesa
ms.author: weijiesa
ms.topic: how-to
ms.date: 08/29/2018
ms.custom:
ms.reviewer: kamaybac   
ms.search.form: InventJournalLossProfit, InventJournalCreate, InventLocationIdLookup 
---

# Adjust stock levels in the warehouse (basic warehousing)

[!include [banner](../../includes/banner.md)]

This procedure walks you through the process of creating and posting an inventory adjustment journal in order to adjust stock levels of products in the warehouse. You need to have an inventory journal name set up for inventory adjustments before you start this. You can walk through this procedure in demo data company USMF, or using your own data. These tasks would normally be carried out by a warehouse employee.

## Create an inventory adjustment journal

1. Go to **Inventory management** \> **Journal entries** \> **Items** \> **Inventory adjustment**.
2. Select **New**.
3. In the **Name** field, select the drop-down button to open the lookup.
4. In the list, select on the inventory adjustment journal name you want to use. Some other fields are populated based on the setup of the inventory adjustment journal name you select.  
5. Select **OK**.

## Create journal lines

1. Select **New**.
2. In the list, mark the item number field.
3. In the **Item number** field, select an item. If you're using demo data company USMF, type *D0001*.
4. In the **Site** field, select the drop-down button to open the lookup.
5. In the list, select a site.
6. In the **Warehouse** field, select the drop-down button to open the lookup.
7. In the list, select a warehouse. If you selected an item with location as a mandatory dimension, you must specify the location here.  
8. In the **Quantity** field, enter a number. The cost price field specifies the cost per unit for inventory receipts. If the cost isn't specified for the item number or if you wanted to change it manually, you would do this here.  

## Validate and post the inventory adjustment journal

1. Select **Validate**.
2. Select **OK**.
3. Select **Post**. When you post this kind of journal, an inventory receipt or issue is posted, the inventory level and value are changed, and ledger transactions are generated.  
4. Select **OK**.
5. Close the form.
6. Close the page.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
