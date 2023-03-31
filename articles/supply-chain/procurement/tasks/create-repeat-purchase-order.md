--- 
# required metadata 
 
title: Create a repeat purchase order
description: This article shows you how to create a repeat purchase order (PO) by copying lines from an earlier purchase order document to a new PO or to an existing PO. 
author: GalynaFedorova
ms.date: 09/30/2020
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: PurchTable, PurchTablePart, PurchCreateOrder, PurchCopying   
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
# Create a repeat purchase order

[!include [banner](../../includes/banner.md)]

This article shows you how to create a repeat purchase order (PO) by copying lines from an earlier purchase order document to a new PO or to an existing PO. There are two methods for creating repeat orders. You can use the actions available at the document level from the Action Pane, or you can use the line detail actions. The document level actions are intended for creating a new purchase order by adding lines and header information from another order, while the line details action is mainly for adding lines to an existing order. The example shown in this guide can be used in the USMF demo data company. This task would typically be carried out by a purchasing agent.

## Create a new repeat purchase order

1. In the navigation pane, go to **Procurement and sourcing \> Purchase orders \> All purchase orders**. First we'll try the option for copying information to a new order.  
1. Select **New**.
1. In the **Vendor account** field, enter `US-101`.
1. Select **OK**.
1. On the Action Pane, open the **Purchase order** tab and, from the **Copy** group, select **From all**. The **Copy from other documents** dialog opens. From here, you can copy from existing orders to your order. There are different options for how the lines are copied, and different kinds of documents that you can copy from. We'll look at the options for how lines are copied first.
1. Expand the **Parameters** FastTab.

    - The **Quantity factor** field is useful if you need to use a quantity that is different than the one that's on the order that you're copying from. For instance, if you want to order twice the quantity that's in the lines that you're copying from, you'd type '2' in this field and then the system will add lines where the original quantity has been doubled.  
    - The **Invert sign** field also supports changing the ordered quantity by changing the sign of the quantity for order lines that are added. This may be useful if you need to reverse a transaction, by creating order lines that negate the transaction. This option is automatically selected when the page is opened from the **Create credit note** action.  
    - The **Copy charges** option allows you to copy charges to your new order from the document that you're copying the order lines from.  
    - The **Recalculate prices** option uses the current prices and discounts rather than copying these from the document that you're copying other information from.  
    - The **Copy precisely** option copies the values of several fields on the order header and lines. If this option isn't selected, default values will be used for many of the fields relating to the vendor and products, just like when you create a new order manually. For example, if you set **Copy precisely** to *Yes* and copy an order that overrides the default invoice account for the vendor, then that same invoice account will be copied to your new order. If you set **Copy precisely** to *No*, the default invoice account for the vendor would be used on your new order instead. Values for the following fields are copied when **Copy precisely** is set to *Yes*:
        - Language
        - Terms of payment
        - Method of payment
        - Payment specification
        - Number sequence group
        - Cash discount
        - Discount percentage
        - Currency
        - Delivery terms
        - Mode of delivery
        - Dimension
        - Sales tax group
        - Override sales tax
        - Prices include sales tax
        - Transport
        - Port
        - Statistics procedure
        - Template ID
        - Delivery name
        - Postal address
        - Reference
        - Reference Table ID
    - The **Delete purchase lines** option deletes all purchase order lines that already exist on the purchase order that you're copying to, before applying the new lines. Use this option with caution, as it deletes all existing lines without further warning.  
    - If you use the **Copy order header** option, you don't need to manually create the header information on your new order. This option will result in default values being used for the fields associated with the vendor. If the document that you're copying from has non-default values that you want to copy, use the **Copy precisely** option as well.
    - There are different document sources that you can copy from, and each has a separate section on this page. For example, the **Purchase orders** section allows you to copy from existing purchase orders.  

1. In the **Purchase orders** section, select the lines you'd like to be copied to your clipboard. It's possible to select additional purchase orders lines from other purchase orders and copy them to your order as well. It's also possible to add lines from other kinds of purchase documents. The next few steps review the different options.  
1. Expand the **Confirmation** section. Here you can select purchase order confirmations to copy from. The purchase order confirmations are identified by the associated purchase journal ID or the purchase order ID.  
1. Expand the **Product receipts** section. Here you can select product receipt journals to copy from. The product receipt journals are identified by the product receipt voucher or the purchase order ID.
1. Expand the **Invoices** section. Here you can select vendor invoices to copy from. The invoices are identified by the invoice voucher or the purchase order ID.
1. Expand the **Selected lines or header to be copied** section. This view shows a summary of all documents and lines that have been selected to be copied to your order.
1. Select **OK**. The lines that you selected have been copied to your new purchase order.

## Copy lines to an existing purchase order  

Instead of copying an entire order, it's more common to create a new PO and complete information on the PO header, and then copy individual lines from existing orders.  

1. Select **Purchase order** line.
1. Select **From all**. The page that opens is identical to the one shown before, but different options are selected when it's opened from the order lines view. Let's review the parameters.
1. Expand the **Parameters** section.

    - The **Delete purchase lines** option isn't selected. This means that you can copy new lines to your order without removing existing lines.
    - The **Copy order header** option is also not selected, as we're only adding additional lines to the order.
    - For this example, we'll copy lines from an existing purchase order.

1. Select the line for the desired purchase order. Notice that the single order line that's on this PO is also selected.  
1. Select **OK**. The additional order line has been added to your purchase order.  

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]