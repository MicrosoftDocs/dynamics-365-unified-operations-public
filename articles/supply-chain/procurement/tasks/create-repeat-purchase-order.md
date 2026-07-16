---
title: Create a repeat purchase order
description: Learn how to create a repeat purchase order (PO) by copying lines from an earlier purchase order document to a new PO or to an existing PO. 
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form: PurchTable, PurchTablePart, PurchCreateOrder, PurchCopying 
ms.topic: how-to
ms.date: 05/28/2026
ms.custom: 
  - bap-template
---

# Create a repeat purchase order

[!include [banner](../../includes/banner.md)]

This article shows you how to create a repeat purchase order (PO) by copying lines from an earlier purchase order document to a new PO or to an existing PO. You can create repeat orders by using two methods. Use the actions available at the document level from the Action Pane, or use the line detail actions. The document level actions are intended for creating a new purchase order by adding lines and header information from another order, while the line details action is mainly for adding lines to an existing order. You can use the example shown in this guide in the USMF demo data company. A purchasing agent typically carries out this task.

## Create a new repeat purchase order

1. In the navigation pane, go to **Procurement and sourcing > Purchase orders > All purchase orders**. First, try the option for copying information to a new order.  
1. Select **New**.
1. In the **Vendor account** field, enter *US-101*.
1. Select **OK**.
1. On the Action Pane, open the **Purchase order** tab and, from the **Copy** group, select **From all**. The **Copy from other documents** dialog opens. From here, you can copy from existing orders to your order. There are different options for how the lines are copied, and different kinds of documents that you can copy from. See the options for how lines are copied first.
1. Expand the **Parameters** FastTab.

    - The **Quantity factor** field is useful if you need to use a quantity that is different from the one on the order that you're copying from. For example, if you want to order twice the quantity that's in the lines that you're copying from, type `2` in this field and then the system adds lines where the original quantity is doubled.  
    - The **Invert sign** field also supports changing the ordered quantity by changing the sign of the quantity for order lines that are added. This change might be useful if you need to reverse a transaction, by creating order lines that negate the transaction. This option is automatically selected when the page is opened from the **Create credit note** action.  
    - The **Copy charges** option allows you to copy charges to your new order from the document that you're copying the order lines from.  
    - The **Recalculate prices** option uses the current prices and discounts rather than copying these values from the document that you're copying other information from.  
    - The **Copy precisely** option copies the values of several fields on the order header and lines. If you don't select this option, default values are used for many of the fields relating to the vendor and products, just like when you create a new order manually. For example, if you set **Copy precisely** to *Yes* and copy an order that overrides the default invoice account for the vendor, then that same invoice account is copied to your new order. If you set **Copy precisely** to *No*, the default invoice account for the vendor is used on your new order instead. Values for the following fields are copied when **Copy precisely** is set to *Yes*:
        - **Language**
        - **Terms of payment**
        - **Method of payment**
        - **Payment specification**
        - **Number sequence group**
        - **Cash discount**
        - **Discount percentage**
        - **Currency**
        - **Delivery terms**
        - **Mode of delivery**
        - **Dimension**
        - **Sales tax group**
        - **Override sales tax**
        - **Prices include sales tax**
        - **Transport**
        - **Port**
        - **Statistics procedure**
        - **Template ID**
        - **Delivery name**
        - **Postal address**
        - **Reference**
        - **Reference Table ID**
    - The **Delete purchase lines** option deletes all purchase order lines that already exist on the purchase order that you're copying to, before applying the new lines. Use this option with caution, as it deletes all existing lines without further warning.  
    - If you use the **Copy order header** option, you don't need to manually create the header information on your new order. This option results in default values being used for the fields associated with the vendor. If the document that you're copying from has non-default values that you want to copy, use the **Copy precisely** option as well.
    - There are different document sources that you can copy from, and each has a separate section on this page. For example, the **Purchase orders** section allows you to copy from existing purchase orders.  

1. In the **Purchase orders** section, select the lines you want to copy to your clipboard. You can select additional purchase order lines from other purchase orders and copy them to your order as well. You can also add lines from other kinds of purchase documents. The next few steps review the different options.  
1. Expand the **Confirmation** section. Here you can select purchase order confirmations to copy from. The purchase order confirmations are identified by the associated purchase journal ID or the purchase order ID.  
1. Expand the **Product receipts** section. Here you can select product receipt journals to copy from. The product receipt journals are identified by the product receipt voucher or the purchase order ID.
1. Expand the **Invoices** section. Here you can select vendor invoices to copy from. The invoices are identified by the invoice voucher or the purchase order ID.
1. Expand the **Selected lines or header to be copied** section. This view shows a summary of all documents and lines that you selected to copy to your order.
1. Select **OK**. The lines that you selected are copied to your new purchase order.

## Copy lines to an existing purchase order  

Instead of copying an entire order, it's more common to create a new PO and complete the information on the PO header. Then, copy individual lines from existing orders.  

1. Select **Purchase order** line.
1. Select **From all**. The page that opens is identical to the one shown earlier, but different options are selected when you open it from the order lines view. Review the parameters.
1. Expand the **Parameters** section.

    - The **Delete purchase lines** option isn't selected. This setting means that you can copy new lines to your order without removing existing lines.
    - The **Copy order header** option isn't selected, as you're only adding extra lines to the order.
    - For this example, copy lines from an existing purchase order.

1. Select the line for the desired purchase order. Notice that the single order line on this PO is also selected.  
1. Select **OK**. The extra order line is added to your purchase order.  

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
