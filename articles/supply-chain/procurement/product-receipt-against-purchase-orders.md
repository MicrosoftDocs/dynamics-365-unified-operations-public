---
title: Product receipt against purchase orders
description: Learn about the various options for registering products as received, including an outline on preregistration and registration.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form: PurchTable, PurchTablePart, VendPackingSlipJournalListPage, VendPackingSlipJournal
ms.topic: how-to
ms.date: 07/21/2025
ms.custom:
- bap-template
---

# Product receipt against purchase orders

[!include [banner](../includes/banner.md)]

This article describes the various options for registering products as received.

Product receipt is the process of recording that products that were ordered were received so that the purchase order (PO) lines can be processed for invoicing. In some cases, products go through preregistration, where additional information from the supplier is recorded before the products are received. When products arrive, they're first marked as **Registered**. The products might then go through other processes, such as quality management, before they're finally marked as **Received**.

## Preregistration (ASN)

Suppliers might share information about products that will be shipped. In this case, you can preregister the products to record this information before the products are received. By preregistering products, you reduce the amount of work that is required during item registration and receipt. Suppliers can provide product information electronically through an Advance Shipment Notice (ASN) that is then automatically recorded in the system. The information in the ASN includes the quantity of products that will be shipped and the date when they'll be shipped. The ASN might also include information such as batch or serial numbers. Registration of the ASN occurs in the **Transportation management** module.

## Registration

Product receipt registration often occurs at the inbound docks in a warehouse. It’s performed either by using a hand-held device or through arrival journals. Alternatively, you can manually register product receipt by using the **Registration** action on the **Purchase order** page. In both cases, the products are marked as *Registered*. The products aren’t yet marked as *Received*.  

Products that are received in a warehouse might go through quality inspection before they're put away into inventory. Either quality orders or quarantine orders can be used to perform quality inspection. If quality orders are used, you can configure the process to temporarily block products through a reservation while they're inspected. If quarantine orders are used, products are moved to another warehouse for inspection. This warehouse is known as the quarantine warehouse. In both quality inspection processes, some of the goods might be scrapped, either because they don’t conform to the quality expectations or because the quality inspection involves destructive testing of a sample of the product.

## Product receipt

Most often, the **Product receipt** action on the **Purchase orders** page is used to mark products as *Received* on the PO. The **Posting product receipt** page has various options for the quantity that is accounted as received. For example, you can set the **Quantity** field to *Ordered quantity* or *Receive now quantity*. Alternatively, if a warehouse arrival process has been used, you'll often set this field to *Registered quantity*. You can modify the quantities on each order line that will be marked as *Received*, to account for any discrepancies, such as under-delivery and over-delivery. During product receipt, you must specify a product receipt identifier, which is typically a reference to the packing slip from the supplier. This identifier is required for accounting, because it enables checks or audits of supplier packing slips against what has been received, and the accounted inventory or expense.  

POs can be created for products that aren’t intended as inventory but are considered an expense. This category includes order lines where the products are marked as *Not stocked* by their inventory model group, and also lines that use procurement categories. In this case, the items might not go through arrival registration and receipt in the warehouse. Instead, the **Product receipt** action is used to record the receipt directly on the PO, and the receipt is based on the ordered quantity, not a registered quantity.  

You can create PO lines where the **New fixed asset** option is enabled. This option indicates that the purchase should be considered a fixed asset instead of inventory. In this case, the fixed asset determination rules that have been configured determine whether the purchase of the product or category exceeds specific thresholds, and must therefore be accounted for as an asset and go through fixed asset management. Purchases can also be made toward an existing fixed asset. In this case, the amount is adjusted as appropriate.  

You can select multiple orders and process receipt on all those orders together. This approach isn’t used often, but you might want to use it if a supplier has consolidated shipments for you into a single load. During product receipt on the purchase, there's a function for doing summary updates. Summary updates let you post a single packing slip from the supplier for more than one PO.  

POs might be created from a sales order where the **Direct delivery** option was selected. When direct delivery is used, the products never arrive in your warehouse but are shipped directly from the supplier to the customer. In this case, the receipt is usually recorded directly on the PO. The receipt can be done automatically, such as through electronic data interchange (EDI) integration with the supplier. Alternatively, if the PO is an intercompany PO, Supply Chain Management automates the receipt on the intercompany sales order when shipment occurs. When direct delivery is used, products are still accounted as inventory, even though they don’t physically arrive at the warehouse. Therefore, when product receipt is registered on the PO, the sales order is automatically updated with a packing slip, so that the overall change to inventory is 0 (zero). In direct delivery scenarios, you shouldn't require preregistration. If you’re using warehouses that are enabled for warehouse management, you can get around the requirement for license plate registration by specifying a virtual warehouse instead. You specify this warehouse in the **Direct delivery warehouse** field on the product.

After the product receipt has been processed on the PO, the PO status is set to *Received* to indicate that the invoice can be processed for the order. You can review details about products that have already been received by using the **Product receipt journals** page.  

You can access this page from the **Receipt** action group on the **Purchase order** page. The information in the journals includes details about the quantities, dates, and dimensions.

## Auto posting product receipts

To automatically post product receipts for multiple purchase orders, follow these steps.

1. Go to **Procurement and sourcing** \> **Purchase orders** \> **Receiving products** \> **Post Product receipt**.
1. In the **Posting product receipt** dialog, on the **Settings** FastTab toolbar, select **Select**.
1. In the **Purchase update** dialog, use the **Range** tab to specify selection criteria for finding the purchase orders you want to post.
1. Select **OK** to return to the **Posting product receipt** dialog. The purchase orders that match the criteria you specified are displayed on the **Overview** FastTab.
1. On the **Overview** FastTab, enter the product receipt identifier in the **Product receipt** column for each purchase order in the grid. This information enables the system to post the product receipt.

    A product receipt identifier must be specified when each product is received. It's typically a reference to the packing slip from the supplier. This identifier is required for accounting because it enables supplier packing slips to be checked against what was received and against the accounted inventory or expense.

1. Select **Batch** to open the **Batch processing** dialog, where you can set up the [batch job](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) that will do the posting.

1. Select **OK** to return to the **Posting product receipt** dialog.
1. Select **OK** to close the **Posting product receipt** dialog.

After the system finishes processing product receipts for all lines in the purchase order, it sets the purchase order status to *Received* to indicate that the invoice can now be processed for the order.

To correct or cancel a product receipt, follow these steps.

1. Go to **Procurement and sourcing** \> **Purchase orders** \> **Receiving Products** \> **Product receipt**. The **Product receipt journal** page opens.
1. On the **Overview** tab, select the product receipt that you want to correct or cancel.
1. On the **Overview** tab toolbar, select **Correct** to make corrections or **Cancel** to cancel the product receipt.

> [!NOTE]
> When correcting a product receipt, you can only reduce the received quantity. To raise the quantity, you must post a new product receipt journal.

## Auto post product receipts when using WMS

Auto posting works differently if you're using warehouse management processes (WMS). Learn more in [Warehouse handling of inbound loads for purchase and inbound shipment orders](../warehousing/inbound-load-handling.md).

## Related information

- [Warehouse handling of inbound loads for purchase and inbound shipment orders](../warehousing/inbound-load-handling.md)
- [Purchase order overview](purchase-order-overview.md)
- [Create purchase orders](purchase-order-creation.md)
- [Approve and confirm purchase orders](purchase-order-approval-confirmation.md)
- [Overview of vendor invoices](../../finance/accounts-payable/vendor-invoices-overview.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
