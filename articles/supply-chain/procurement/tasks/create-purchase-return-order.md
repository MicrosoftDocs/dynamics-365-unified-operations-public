---
title: Create a purchase return order
description: Learn how to create a purchase return order (return PO) by using the Credit note action to copy lines from a vendor invoice document to a new purchase order. 
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form: PurchTable, PurchTablePart, PurchCreateOrder, PurchCopying, InventMarking, PurchEditLines 
ms.topic: how-to
ms.date: 09/02/2025
ms.custom: 
  - bap-template
---

# Create a purchase return order

[!include [banner](../../includes/banner.md)]

Use purchase return orders (return POs) when you need to send goods back to a vendor. Here are a few common scenarios where you might create a return PO:

- You received goods that need to be returned
- You created an invoice but didn't receive the goods
- You need to return some of the goods that you received (partial return of goods)
- You received items that weren't ordered (unplanned receipt)
- Vendor buyback or consignment return

This article explains how to create a return PO by using the **Credit note** action to copy lines from a vendor invoice document to a new purchase order. It also shows you how to confirm the order and process shipment of the goods back to the vendor. A purchasing agent typically carries out this task.

## Create a new return PO

1. Go to **Procurement and sourcing** \> **Purchase orders** \> **All purchase orders**. The first step is to create a new purchase order to use as the return PO.  
1. Select **New**.
1. In the **Vendor account** field, specify the vendor you're returning to.
1. Select **OK**.
1. On the Action Pane, select **Purchase**.
1. Select **Credit note**. This page lets you copy from an existing vendor invoice to your return order. This page is the same page that's used for other copy actions. But because you opened it from the **Credit note** action, the page is configured to support the creation of a return order that offsets vendor invoices.  
1. Expand the **Parameters** section.
    - The **Invert sign** option is automatically selected, and you can't change it. This option ensures that the sign is changed for the quantities, and that order lines that you add offset the vendor invoice.  
    - The **Copy charges** option is automatically selected, and you can't change it. This option means that charges from the vendor invoice are added to the return PO to offset the original charge. You can modify the changes on the order header and lines later.  
    - The **Copy precisely** option is automatically selected, and you can't change it. This option ensures that an exact copy is made of the values in all the fields on the vendor invoice header and lines. This option means that a return PO is created with values that match all terms used with the vendor invoice document.
    - The **Delete purchase lines** option deletes any purchase order lines that already exist on the purchase order before adding the new lines. In this example, you didn't yet add any lines to the return PO, so this option has no effect. Use this option with caution, as it deletes all existing lines without further warning.  
    - The **Copy order header** option is automatically selected, and you can't change it. This option ensures that information is copied from the vendor invoice and applied to the return PO header. This option is useful because it helps to ensure that the return PO offsets the invoice by using similar terms.  
1. Collapse the **Parameters** section.
1. Expand the **Invoices** section. You opened the page from the **Credit note** action, so the only option available is to copy information from vendor invoices. This tab shows all the available invoices for the vendor account that you specified on the return PO. The invoices are identified by the invoice voucher or the purchase order IDs.
1. Find the vendor invoice that includes the items you want to return and highlight it by selecting any field in that line.
1. Select the check box for the line. The lines available on the vendor invoice are automatically selected together with the order.
1. Highlight the line for the item you want to return by selecting any field in that line. In the **Quantity** field, enter the quantity that you want to return to the vendor.
1. Clear the check box for each line that you don't want to return items for. Only the lines that you select are copied to your order.
1. Collapse the **Invoices** section.
1. Expand the **Selected lines or header to be copied** section. This view shows a summary of all the documents and lines that you selected to copy to your order.  
1. Collapse the **Selected lines or header to be copied section**.
1. Select **OK**. The line that you selected is now copied to your return PO. The **Quantity** field shows a negative value for each item you're returning.
1. In the **Purchase order line** section, select **Inventory**.
1. Select **Marking**. The order line that you created is marked against the inventory transaction from the vendor invoice. This marking ensures that the inventory that's returned to the vendor is the same as the inventory that was received from them earlier. There are some situations where marking doesn't occur, for example, if the inventory is already marked as *Consumed*, or if the product is one that doesn't use marking.  
1. Select **OK**.

## Confirm and record the shipment of goods

1. Select **Actions** \> **Confirm**.
1. On the Action Pane, select **Receive**.
1. Select **Product receipt**.
    - Use this page to record product receipt for purchase orders and to process the return of goods back to the vendor. Order lines with a negative quantity mean that goods are to be returned to the vendor, and the document that you can generate from this page can be used as packing slip for this use.
    - In the **Quantity** field, select *Ordered quantity*. This step ensures that the shipment processes the full ordered quantity that the order lines include.
1. In the **Product receipt** field, type a value. Use this field to enter a reference that acts as a voucher for the product receipt journal.  
1. Select **OK**. The goods are now recorded as shipped on the return PO, and a product receipt journal is created. Use the Product receipt action to review the journals created with the purchase order, and see what was received or returned, and when.  

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
