--- 
# required metadata 
 
title: Create a purchase return order
description: This procedure shows you how to create a purchase return order by using the Credit note action to copy lines from a vendor invoice document to a new PO. 
author: GalynaFedorova
ms.date: 06/25/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: PurchTable, PurchTablePart, PurchCreateOrder, PurchCopying, InventMarking, PurchEditLines   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: gfedorova
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create a purchase return order

[!include [banner](../../includes/banner.md)]

This procedure shows you how to create a purchase return order by using the Credit note action to copy lines from a vendor invoice document to a new PO. It also shows you how to confirm the order and process shipment of the goods back to the vendor. The example shown in this procedure can be used in the USMF demo data company. This task would typically be carried out by a purchasing agent.

## Create a new purchase return order
1. Go to **Procurement and sourcing > Purchase orders > All purchase orders**. The first step is to create a new purchase order to be used as the purchase return order.  
2. Click **New**.
3. In the **Vendor account** field, enter "US-102".
4. Click **OK**.
5. On the **Action Pane**, click **Purchase**.
6. Click **Credit note**. This is the page from which you can copy from an existing vendor invoice to your return order. This is the same page that's used for other copy actions. But because we've opened it from the Credit note action, the page is configured to support the creation of a return order that offsets vendor invoices.  
7. Expand the **Parameters** section.
    - The **Invert sign** option is automatically selected, and cannot be changed. This ensures that the sign is changed for the quantities, and that order lines that are added will offset the vendor invoice.  
    - The **Copy charges** option is automatically selected, and cannot be changed. This means that charges from the vendor invoice are added to the purchase return order to offset the original charge. It's possible to modify the changes on the order header and lines later.  
    - The **Copy precisely** option is automatically selected, and cannot be changed. This ensures that an exact copy is made of the values in all the fields on the vendor invoice header and lines. This means that a purchase return order is created with values that match all terms used with the vendor invoice document. 
    - The **Delete purchase lines** option deletes any purchase order lines that already exist on the purchase order before adding the new lines. In this example we have not yet added any lines to the purchase return order, so there wouldn't be any effect. Use this option with caution, as it deletes all existing lines without further warning.  
    * The **Copy order header** option is automatically selected, and cannot be changed. This ensures that information is copied from the vendor invoice and applied to the purchase return order header. This is useful because it helps to ensure that the purchase return order offsets the invoice by using similar terms.  
8. Collapse the **Parameters** section.
9. Expand the **Invoices** section. The page has been opened from the Credit note action, so the only option available is to copy information from vendor invoices. This tab shows all the available invoices for the vendor account that's specified on the purchase return order that you created earlier.   The invoices are identified by the invoice voucher or the purchase order IDs.
10. Locate the vendor invoice identified by invoice number AP-0006, and highlight that line by clicking on any field in that line.
11. Select the line by clicking in the check box for the line. Notice that the lines available on the vendor invoice are automatically selected together with the order. This particular vendor invoice has 2 order lines. For this example, we'll return part of the quantity from the second line.
12. Highlight the second line (the one with item M0006) by clicking on any field in that line.
13. In the **Quantity** field, change the quantity to 10. This is the quantity that we'll return to the vendor. 
14. Highlight the first line (the one with item M0005) by clicking on any field in that line.
15. Clear the check box for the line. Only the lines that you've selected will be copied to your order.
16. Collapse the **Invoices** section.
17. Expand the **Selected lines or header to be copied** section. This view shows a summary of all the documents and lines that you've selected to be copied to your order.  
18. Collapse the **Selected lines or header to be copied section**.
19. Click **OK**. The line that you selected has now been copied to your purchase return order. The **Quantity** field shows -10.   
20. In the **Purchase order line** section, click **Inventory**.
21. Click **Marking**. The order line that was created is marked against the inventory transaction from the vendor invoice. This ensures that the inventory that's returned to the vendor is the same as the inventory that was received from them earlier. There are some situations where marking does not occur, for example, if the inventory has already been marked as Consumed, or if the product is one that doesn't use marking.  

22. Click **OK**.

## Confirm and record the shipment of goods
1. Click **Actions > Confirm**.
2. On the **Action Pane**, click **Receive**.
3. Click **Product receipt**.
    - This page is used to record product receipt for purchase orders and also to process the return of goods back to the vendor. Order lines with a negative quantity mean that goods are to be returned to the vendor, and the document that can be generated from this page can be used as packing slip for this use.   
    - In the **Quantity** field, select Ordered quantity for this example. This ensures that the shipment will be processed for the full ordered quantity that the order lines were created with.   
4. In the **Product receipt** field, type a value. This field is used to enter a reference that will be used as a voucher for the product receipt journal.  
5. Click **OK**. The goods have now been recorded as shipped on the purchase return order, and a product receipt journal has been created. You can use the Product receipt action to review the journals created with the purchase order, and see what was received or returned, and when.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]