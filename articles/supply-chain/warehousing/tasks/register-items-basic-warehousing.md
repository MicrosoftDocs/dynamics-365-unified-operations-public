--- 
title: Register items for a basic warehousing enabled item using an item an item arrival journal
description: Learn how to register items using the item arrival journal when you are using "basic warehousing" in the Inventory management module.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 08/29/2018
ms.custom:
ms.reviewer: kamaybac    
ms.search.form: PurchTable, PurchTablePart, PurchCreateOrder, WMSJournalTable, WMSJournalCreate, PurchEditLines 
---

# Register items for a basic warehousing enabled item using an item an item arrival journal

[!include [banner](../../includes/banner.md)]

This procedure shows you how to register items using the item arrival journal when you are using "basic warehousing" in the Inventory management module. This would usually be done by a receiving clerk. You can run this procedure in demo data company USMF with the example values that are shown.  If you are not using USMF, you need to have a confirmed purchase order with an open purchase order line before you start this guide. The item on the line must be stocked. And the item needs to be associated with a storage dimension group, where site and warehouse are active.

## Create item arrival journal header

1. Go to **Inventory management** \> **Journal entries** \> **Item arrival** \> **Item arrival**.
2. Select **New**.
3. In the **Name** field, type a value. If you are using USMF, you can type *WHS*. If you're using other data, the journal whose name you choose has to have the following properties: **Cheque picking location** must be set to *No*, and **Quarantine management** must be set to *No*.  
4. In the **Packing slip** field, type a value. This is the packing slip ID from the packing slip issued by the vendor. Add a unique number.  
5. In the **Number** field, select the purchase order.
6. Select **OK**.

## Add lines to item arrival journal

1. Select **Functions**.
2. Select **Create lines**. The lines can be entered manually into this journal or created automatically. This will show you how to create this automatically.  
3. Select or clear the **Initialize quantity** checkbox. This initializes the quantity on the journal lines with the quantity not registered from the purchase order line.  
4. Select **OK**.

## Post the journal

1. Select **Post**.
2. Select **OK**.

## Generate the product receipt

1. Select **Functions**.
2. Select **Product receipt**.
3. Select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
