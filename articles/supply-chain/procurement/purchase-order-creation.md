---
title: Create purchase orders
description: This article describes the process and options when you manually create a purchase order.
author: GalynaFedorova
ms.author: gfedorova
ms.reviewer: kamaybac
ms.search.form: PurchTable, PurchTablePart
ms.topic: how-to
ms.date: 01/09/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Create purchase orders

[!include [banner](../includes/banner.md)]

This article describes the process and options when you manually create a purchase order.

When you create a purchase order (PO), general information about the whole order is specified in the PO header, and you then add one or more PO lines. This article describes some of the most frequently used options that are available.  

You can also create POs by copying lines from another PO document or a sales order. In this case, you can reverse the sign on the inventory, as you would reverse the sign on an invoice to indicate credit.  

Although you can manually create POs, they're more typically generated from other processes. Orders can be automatically created based on other documents, such as requisitions. Alternatively, they can be created as part of the master planning process through planned POs. If you use purchase agreements, POs can be created by the **Release order** action. There are also more advanced methods for automatically creating a PO. For example, orders can be created when you use direct delivery or intercompany order chains.

## Creating a purchase order header

When you create a new PO, a dialog box appears, where you can enter the most common information for the PO header. When you select **OK** to close the dialog box, the order is created, and you can then specify additional information in the header.  

The first detail that you must consider when you create a PO is the type of order. The **Purchase order** type is used most often. However, if a credit invoice is required, you can use the **Returned order** type.  

You must specify the supplier in the **Vendor account** field. For this field, you can search on either the account or the vendor name. If a vendor delivers from multiple locations but uses a single invoice account, you can select that invoice account in the **Invoice account** field and then use it with different vendor accounts. If you must create a PO for products that won't be ordered repeatedly, you can use the **One-time supplier** option. This option automatically creates a new vendor account that is marked as a one-time account, to support a later clean-up process for one-time accounts in the **Accounts payable** module. When you select a vendor account, many fields in the PO header inherit default values from the information that is associated with the vendor account. For example, the default delivery site and warehouse are copied from the vendor information. However, you can override these default values if the purchase is intended for another location.  

If the supplier has provided a reference number for the order, you can record this information in the **Vendor reference** field. For returned orders, you must specify a value in the **RMA** field to reference the supplier's authorization for processing the return.  

If a purchase agreement is associated with the order, you must specify this information in the **Purchase agreement** field.  

The PO header also contains information about charges that apply to the whole order instead of individual lines. Charges can be automatically added to the order if automatic charges have been set up for the vendor or the vendor's charge group. You can also manually add charges to the order header by selecting **Maintain charges** on the Action Pane.

## Adding purchase order lines

POs can be for physical products or for services. A setting on the inventory model group determines whether a particular item number applies to a product or a service. Usually, the item that is purchased is specified by an item number. However, if the order is for products or services that are directly consumed, you can also specify the item by using a procurement category.  

PO lines contain lots of fields, but many of these fields have a default value or a value that is inherited from the order header. Additional fields are set when you select a product or service. The fields that are most often set manually include the fields for the item number, quantity, and requested delivery date. Information about unit price and discounts is also important, but the values of those fields are often determined by trade agreements or purchase agreements.  

When you select a product, you can search on all or part of the product name instead of using the item number. If the product has several variants, such as different sizes, you can see an overview of the available variants by using the **Add lines** function or by using the lookup that is available in the **Variant number** field.  

Often, you'll have to specify several dimensions for the item that is selected on each PO line. The dimensions that must be specified depend on the dimension groups that have been assigned to the product master definition. For example, you'll often have to specify a site and warehouse to indicate the location that the product should be delivered to. You identify product variants by specifying a variant number, or by entering values for one or more product dimensions, such as color, size, configuration, or style. Tracking dimensions, such as batch and serial number, let you uniquely identify each inventory lot. After you've created an order, you can capture dimension values on the order by using the **Registration** action. For example, you've ordered a quantity of five pieces of an item. Later, you register that three of those pieces will be black, and two of them will be blue. This approach is an alternative to capturing the dimension information during arrival registration.  

You can check the details of the inventory transaction status for stocked products. For example, you might want to check the on-hand inventory to help you decide how much to order. Alternatively, you might want to review the inventory status of an ordered quantity to see whether inbound arrival registration has occurred.  

A PO line that is being used to return a product to the vendor will have a negative quantity. You can select a specific lot to return by using the **Reservation** action.  

Sometimes, you might want to divide the quantity that you've ordered, so that different parts of it are delivered on different dates. You can set up these deliveries by using the **Delivery schedule** action, which is available on the **Purchase order line** menu in the **Lines** view.  

Charges can be automatically added to PO lines, if automatic charges have been set up for the vendor or vendor charge group, and for the item or item charge group. However, more typically, charges are added manually at the order line level. To add a charge, open the **Maintain charges** page by using the **Maintain charges** action on the **Financials** menu in the **Lines** view. The advantage of adding charges directly at the order line level is that the charge can be allocated as an inventory cost. To set up charge codes to account product cost, use the **Item** debit option. These types of charges must be allocated from the PO header to the lines before the order can be confirmed. For example, you might want to allocate charges based on the quantity on each line. The charge category also affects how charges are accounted. For example, fixed charges specify a fixed amount, and percent charges are calculated as a percentage of the net amount for the order line. POs can be assigned to a load, and the load might include an estimate of the expected expense for the transportation cost. You can allocate this expense from the load back to the PO lines.

## Purchase order actions

After you've added the header and lines to the PO, you must often complete additional steps before the order is ready to be confirmed. Because so many options are available, you might find it helpful to use [Action search](../../fin-ops-core/fin-ops/get-started/action-search.md) to find the relevant menu item.  

You can configure products on the order so that they have supplementary items. Supplementary items are products that must or can be bought together with other products. Supplementary products might be added free of charge as accompanying products, or you may be able to decide whether to add them to the order or not. You can review the supplementary items after each order line that is added. However, you'll probably find it more convenient to review and add relevant supplementary items for all the order lines by using the **Supplementary items** page, which you can open from the Action Pane.  

Discounts are usually added to lines as they're created. However, a few discounts apply to the whole order:

- The **Total discount** action calculates a total discount percentage that is applied to the full order. Don't confuse this discount with the cash discount percentage. Cash discounts are applied when the invoice is paid, and they depend on payment settlement by a specific date.
- If a multi-line discount applies, you must use the **Multiline discount** action to calculate and assign it to the order. Multi-line discounts are discounts that can be offered if a mix of products on the order exceeds a joint threshold. Only a few companies use this type of discount.

Charges that have a charge code that uses the **Item** debit type must be assigned to the line level before the order can be confirmed. You might find it convenient to assign these charges at the order header level, so that you can specify the total amount of the charge. However, in this case, the charge must then be allocated down to each line before the order can be confirmed. You can use the **Allocate charges** action to split amounts from charges that are assigned at the header level down to the order lines. Charges can be split according to the net amount of each line, according to the quantity that has been ordered, or evenly across the order lines. After you've allocated charges to the lines, the charge is removed from the order header.  

POs can be configured to require that budget funds be allocated to the order before it can be processed. In this case, you can use the **Budget checking** action to allocate the budget.  

You might have to delay the completion of a PO. For example, you might require additional information about products or services, or you might have to get authorization for the spend. There are several ways to hold back an order. For example, you can wait to confirm the order. Alternatively, if a change management workflow is being used, don't submit the order for approval. If you must block all orders for a particular vendor, you can also mark the vendor as *On hold* for processing on the vendor master. There are also circumstances that might prevent the order from being processed. For example, processing might be prevented if credit limits have been exceeded, or if the required budget funds aren't available.

## Additional resources

- [Purchase order overview](purchase-order-overview.md)
- [Approve and confirm purchase orders](purchase-order-approval-confirmation.md)
- [Product receipt against purchase orders](product-receipt-against-purchase-orders.md)
- [Vendor invoices overview](../../finance/accounts-payable/vendor-invoices-overview.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
