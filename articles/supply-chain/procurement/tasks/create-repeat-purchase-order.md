--- 
# required metadata 
 
title: Create a repeat purchase order
description: This procedure shows you how to create a repeat purchase order (PO) by copying lines from an earlier purchase order document to a new PO or to an existing PO. 
author: FrankDahl
manager: AnnBe 
ms.date: 08/23/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: bis
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: fdahl
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create a repeat purchase order

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure shows you how to create a repeat purchase order (PO) by copying lines from an earlier purchase order document to a new PO or to an existing PO. There are two methods for creating repeat orders. You can use the actions available at the document level from the Action Pane, or you can use the line detail actions. The document level actions are mainly intended for creating a new purchase order by adding lines and header information from another order, while the line details action is mainly for adding lines to an existing order. The example shown in this guide can be used in the USMF demo data company. This task would typically be carried out by a purchasing agent.


## Create a new repeat purchase order
1. Go to Procurement and sourcing > Purchase orders > All purchase orders.
    * First we’ll try the option for copying information to a new order.  
2. Click New.
3. In the Vendor account field, enter US-101.
4. Click OK.
5. On the Action Pane, click Purchase order.
6. Click From all.
    * This is the page from which you can copy from existing orders to your order. There are different options for how the lines are copied, and different kinds of documents that you can copy from. We’ll look at the options for how lines are copied first.   
7. Expand the Parameters section.
    * The Quantity factor field is useful if you need to use a quantity that is different than the one that’s on the order that you’re copying from. For instance, if you want to order twice the quantity that’s in the lines that you’re copying from, you’d type ‘2’ in this field and then the system will add lines where the original quantity has been doubled.  
    * The Invert sign field also supports changing the ordered quantity by changing the sign of the quantity for order lines that are added. This may be useful if you need to reverse a transaction, by creating order lines that negate the transaction. This option is automatically selected when the page is opened from the Create credit note action.  
    * The Copy charges option allows you to copy charges to your new order from the document that you’re copying the order lines from.  
    * The Recalculate prices option uses the current prices and discounts rather than copying these from the document that you’re copying other information from.  
    * The Copy precisely option creates an exact copy of the values in all the fields on the order document header and lines. If this option is not selected, default values are used for many of the fields relating to the vendor and products just as if you were creating the new order manually. For example, if the order that you’re copying from had overridden the default Invoice account for the vendor, that same Invoice account would be copied to your order. If you didn’t select the Copy precisely option, the default Invoice account for the vendor would be used on your order instead.  
    * The Delete purchase lines option deletes all purchase order lines that already exist on the purchase order that you’re copying to, before applying the new lines. Use this option with caution, as it deletes all existing lines without further warning.  
    * If you use the Copy order header option, you don’t need to manually create the header information on your new order. Note that this option will result in default values being used for the fields associated with the vendor. If the document that you’re copying from has non-default values that you want to copy, use the Copy precisely option as well.  
8. Collapse the Parameters section.
    * There are different document sources that you can copy from, and each has a separate section on this page. For example, the Purchase orders section allows you to copy from existing purchase orders.  
9. Click on the line for the purchase order that has an ID of 00015. 
10. Select the line by clicking in the check box.
11. Clear the check box for the line so that it is not copied to your order.
    * Now 4 lines have been selected to be copied to your purchase order. It’s possible to select additional purchase orders lines from other purchase orders and copy them to your order as well. It’s also possible to add lines from other kinds of purchase documents. The next few steps review the different options.  
12. Collapse the Purchase orders section.
13. Expand the Confirmation section.
    * Here you can select purchase order confirmations to copy from. The purchase order confirmations are identified by the associated purchase journal ID or the purchase order ID.  
14. Collapse the Confirmation section.
15. Expand the Product receipts section.
    * Here you can select product receipt journals to copy from. The product receipt journals are identified by the product receipt voucher or the purchase order ID.   
16. Collapse the Product receipts section.
17. Expand the Invoices section.
    * Here you can select vendor invoices to copy from. The invoices are identified by the invoice voucher or the purchase order ID.   
18. Collapse the Invoices section.
19. Expand the Selected lines or header to be copied section.
    * This view shows a summary of all documents and lines that have been selected to be copied to your order.   
20. Collapse the Selected lines or header to be copied section.
21. Click OK.
    * The 4 lines that you selected have been copied to your new purchase order.   

## Copy lines to an existing purchase order
    * Instead of copying an entire order, it’s more common to create a new PO and complete information on the PO header, and then copy individual lines from existing orders.  
1. Click Purchase order line.
2. Click From all.
    * The page that opens is identical to the one shown before, but different options are selected when it’s opened from the order lines view. Let’s review the parameters.   
3. Expand the Parameters section.
    * The Delete purchase lines option is not selected. This means that you can copy new lines to your order without removing existing lines.   
    * The Copy order header option is also not selected, as we’re only adding additional lines to the order.   
4. Collapse the Parameters section.
    * For this example, we’ll copy lines from an existing purchase order.   
5. Click on the line for the purchase order that has an ID of 00034. 
6. Select the line by clicking in the check box.
    * Notice that the single order line that’s on this PO is also selected.  
7. Click OK.
    * The additional order line has been added to your purchase order.  

