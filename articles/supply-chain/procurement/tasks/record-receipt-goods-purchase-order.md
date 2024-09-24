---
title: Record the receipt of goods on the purchase order
description: Learn how to record receipt of goods directly on a purchase order, including a step-by-step process for preparing new purchase orders. 
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: PurchTable, PurchTablePart, PurchCreateOrder, InventItemIdLookupPurchase, PurchEditLines
ms.topic: how-to
ms.date: 08/26/2024
ms.custom: 
  - bap-template
---

# Record the receipt of goods on the purchase order

[!include [banner](../../includes/banner.md)]

This article explains how to record receipt of goods directly on a purchase order. It's also possible to register product receipt in the warehouse, and then later record it on the purchase order. This task is typically done by a purchasing agent or an accounts payable coordinator. The example shown in this guide uses values from the USMF demo data company and has you prepare an example purchase order to receive against. If you were using the procedure on your own data, you would start at the *Record receipt of goods* section.

## Prepare a new purchase order for receipt of goods

1. Go to **Procurement and sourcing > Purchase orders > All purchase orders**.
1. Select **New**.
1. In the **Vendor account** field, enter *US-101*.
1. Select **OK**.
1. In the **Item number** field, enter *M0001*.
1. In the **Quantity** field, enter *5*.
1. On the Action Pane, select **Purchase**.
1. Select **Confirm**.

## Record receipt of goods

1. On the Action Pane, select **Receive**.
1. Select **Product receipt**. The **Quantity** field allows you to select different options for the quantity that you want to receive. For example, if a quantity has previously been registered in the warehouse, you can select *Registered quantity*. For this example, use the value *Ordered quantity*.
1. Expand the **Overview** section.
1. In the **Product receipt** field, type any value. This field is used to enter a reference that will be used as voucher for the product receipt journal.  
1. Expand the **Lines** section.
1. Set **Quantity** to *4*. Here you can manually specify the quantity that is being received for each line on the order.  
1. Select **OK**. The goods have now been recorded as received on the purchase order, and a product receipt journal has been created as document to reflect this. You can use the Product receipt action to review the journals created with the purchase order, and see what was received, and when.  

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
