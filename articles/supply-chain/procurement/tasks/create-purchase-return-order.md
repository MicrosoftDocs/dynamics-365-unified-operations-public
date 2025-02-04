---
title: Create a purchase return order
description: Learn how to create a purchase return order by using the Credit note action to copy lines from a vendor invoice document to a new PO. 
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form: PurchTable, PurchTablePart, PurchCreateOrder, PurchCopying, InventMarking, PurchEditLines 
ms.topic: how-to
ms.date: 07/30/2024
ms.custom: 
  - bap-template
---

# Create a purchase return order

[!include [banner](../../includes/banner.md)]

This procedure shows you how to create a purchase return order by using the **Credit note** action to copy lines from a vendor invoice document to a new purchase order. It also shows you how to confirm the order and process shipment of the goods back to the vendor. This task would typically be carried out by a purchasing agent.

## Create a new purchase return order

1. Go to **Procurement and sourcing** \> **Purchase orders** \> **All purchase orders**. The first step is to create a new purchase order to be used as the purchase return order.  
1. Select **New**.
1. In the **Vendor account** field, specify the vendor you're returning to.
1. Select **OK**.
1. On the Action Pane, select **Purchase**.
1. Select **Credit note**. This is the page from which you can copy from an existing vendor invoice to your return order. This is the same page that's used for other copy actions. But because we've opened it from the **Credit note** action, the page is configured to support the creation of a return order that offsets vendor invoices.  
1. Expand the **Parameters** section.
    - The **Invert sign** option is automatically selected, and can't be changed. This ensures that the sign is changed for the quantities, and that order lines that are added will offset the vendor invoice.  
    - The **Copy charges** option is automatically selected, and can't be changed. This means that charges from the vendor invoice are added to the purchase return order to offset the original charge. It's possible to modify the changes on the order header and lines later.  
    - The **Copy precisely** option is automatically selected, and can't be changed. This ensures that an exact copy is made of the values in all the fields on the vendor invoice header and lines. This means that a purchase return order is created with values that match all terms used with the vendor invoice document.
    - The **Delete purchase lines** option deletes any purchase order lines that already exist on the purchase order before adding the new lines. In this example we haven't yet added any lines to the purchase return order, so there wouldn't be any effect. Use this option with caution, as it deletes all existing lines without further warning.  
    - The **Copy order header** option is automatically selected, and can't be changed. This ensures that information is copied from the vendor invoice and applied to the purchase return order header. This is useful because it helps to ensure that the purchase return order offsets the invoice by using similar terms.  
1. Collapse the **Parameters** section.
1. Expand the **Invoices** section. The page has been opened from the **Credit note** action, so the only option available is to copy information from vendor invoices. This tab shows all the available invoices for the vendor account that's specified on the purchase return order that you created earlier. The invoices are identified by the invoice voucher or the purchase order IDs.
1. Locate the vendor invoice that includes the items you want to return and highlight it by selecting any field in that line.
1. Select the check box for the line. Notice that the lines available on the vendor invoice are automatically selected together with the order.
1. Highlight the line for the item you want to return by selecting any field in that line. In the **Quantity** field, enter the quantity that you want to return to the vendor.
1. Clear the check box for each line that you don't want to return items for. Only the lines that you've selected will be copied to your order.
1. Collapse the **Invoices** section.
1. Expand the **Selected lines or header to be copied** section. This view shows a summary of all the documents and lines that you've selected to be copied to your order.  
1. Collapse the **Selected lines or header to be copied section**.
1. Select **OK**. The line that you selected has now been copied to your purchase return order. The **Quantity** field should show a negative value for each item you're returning.
1. In the **Purchase order line** section, select **Inventory**.
1. Select **Marking**. The order line that was created is marked against the inventory transaction from the vendor invoice. This ensures that the inventory that's returned to the vendor is the same as the inventory that was received from them earlier. There are some situations where marking doesn't occur, for example, if the inventory has already been marked as *Consumed*, or if the product is one that doesn't use marking.  
1. Select **OK**.

## Confirm and record the shipment of goods

1. Select **Actions** \> **Confirm**.
1. On the Action Pane, select **Receive**.
1. Select **Product receipt**.
    - This page is used to record product receipt for purchase orders and also to process the return of goods back to the vendor. Order lines with a negative quantity mean that goods are to be returned to the vendor, and the document that can be generated from this page can be used as packing slip for this use.
    - In the **Quantity** field, select *Ordered quantity*. This ensures that the shipment will be processed for the full ordered quantity that the order lines were created with.
1. In the **Product receipt** field, type a value. This field is used to enter a reference that will be used as a voucher for the product receipt journal.  
1. Select **OK**. The goods have now been recorded as shipped on the purchase return order, and a product receipt journal has been created. You can use the Product receipt action to review the journals created with the purchase order, and see what was received or returned, and when.  

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
