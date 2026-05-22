---
title: Product receipt against purchase orders
description: Learn about the various options for registering products as received, including an outline on preregistration and registration.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form: PurchTable, PurchTablePart, VendPackingSlipJournalListPage, VendPackingSlipJournal
ms.topic: how-to
ms.date: 01/27/2026
ms.custom:
  - bap-template
---

# Product receipt against purchase orders

[!include [banner](../includes/banner.md)]

This article describes the various options for registering products as received.

Product receipt is the process of recording that products you ordered are received so that the purchase order (PO) lines can be processed for invoicing. In some cases, products go through preregistration, where you record additional information from the supplier before receiving the products. When products arrive, you first mark them as *Registered*. You might then send the products through other processes, such as quality management, before you finally mark them as *Received*.

## Preregistration (ASN)

Suppliers might share information about products that they'll ship. In this case, you can preregister the products to record this information before receiving the products. By preregistering products, you reduce the amount of work that is required during item registration and receipt. Suppliers can provide product information electronically through an Advance Shipment Notice (ASN) that the system automatically records. The information in the ASN includes the quantity of products that will be shipped and the date when they'll be shipped. The ASN might also include information such as batch or serial numbers. The **Transportation management** module registers the ASN.

## Registration

You often register product receipt at the inbound docks in a warehouse. Workers register receipts using a hand-held device or through arrival journals. Alternatively, you can manually register product receipt by using the **Registration** action on the **Purchase order** page. In both cases, you mark the products as *Registered*. You don't yet mark the products as *Received*.

Products that you receive in a warehouse might go through quality inspection before workers put them away into inventory. Either quality orders or quarantine orders can be used to perform quality inspection. If you use quality orders, you can configure the process to temporarily block products through a reservation while they're inspected. If you use quarantine orders, workers move products to another warehouse for inspection. This warehouse is known as the quarantine warehouse. In both quality inspection processes, workers might scrap some of the goods, either because they don't conform to the quality expectations or because the quality inspection involves destructive testing of a sample of the product.

## Product receipt

Use the **Product receipt** action on the **Purchase orders** page to mark products as *Received* on the purchase order. The **Posting product receipt** page has various options for the quantity that you account as received. For example, you can set the **Quantity** field to *Ordered quantity* or *Receive now quantity*. Alternatively, if a warehouse arrival process is used, set this field to *Registered quantity*. You can modify the quantities on each order line that you mark as *Received*, to account for any discrepancies, such as under-delivery and over-delivery. During product receipt, specify a product receipt identifier, which is typically a reference to the packing slip from the supplier. This identifier is required for accounting, because it enables checks or audits of supplier packing slips against what is received, and the accounted inventory or expense.

Create purchase orders for products that aren't intended as inventory but are considered an expense. This category includes order lines where the products are marked as *Not stocked* by their inventory model group, and also lines that use procurement categories. In this case, the items might not go through arrival registration and receipt in the warehouse. Instead, use the **Product receipt** action to record the receipt directly on the purchase order, and the receipt is based on the ordered quantity, not a registered quantity.

Use the **New fixed asset** option for purchase order lines to indicate that the purchase is a fixed asset instead of inventory. In this case, the fixed asset determination rules that you configure determine whether the purchase of the product or category exceeds specific thresholds, and must therefore be accounted for as an asset and go through fixed asset management. You can also make purchases toward an existing fixed asset. In this case, adjust the amount as appropriate.

You can select multiple orders and process receipt on all those orders together. This approach isn't used often, but you might want to use it if a supplier consolidates shipments for you into a single load. During product receipt on the purchase, there's a function for doing summary updates. Summary updates let you post a single packing slip from the supplier for more than one purchase order.

You might create purchase orders from a sales order where the **Direct delivery** option was selected. When you use direct delivery, the products never arrive in your warehouse but are shipped directly from the supplier to the customer. In this case, you usually record the receipt directly on the purchase order. The receipt can be done automatically, such as through electronic data interchange (EDI) integration with the supplier. Alternatively, if the purchase order is an intercompany order, Supply Chain Management automates the receipt on the intercompany sales order when shipment occurs. When you use direct delivery, you still account products as inventory, even though they don't physically arrive at the warehouse. Therefore, when you register product receipt on the purchase order, the sales order is automatically updated with a packing slip, so that the overall change to inventory is 0 (zero). In direct delivery scenarios, you shouldn't require preregistration. If you're using warehouses that are enabled for warehouse management, you can get around the requirement for license plate registration by specifying a virtual warehouse instead. You specify this warehouse in the **Direct delivery warehouse** field on the product.

After you process the product receipt on the purchase order, the system sets the purchase order status to *Received* to indicate that the invoice can be processed for the order. You can review details about products that are already received by using the **Product receipt journals** page.

You can access this page from the **Receipt** action group on the **Purchase order** page. The information in the journals includes details about the quantities, dates, and dimensions.

## Auto posting product receipts

To automatically post product receipts for multiple purchase orders, follow these steps:

1. Go to **Procurement and sourcing** \> **Purchase orders** \> **Receiving products** \> **Post Product receipt**.
1. In the **Posting product receipt** dialog, on the **Settings** FastTab toolbar, select **Select**.
1. In the **Purchase update** dialog, use the **Range** tab to specify selection criteria for finding the purchase orders you want to post.
1. Select **OK** to return to the **Posting product receipt** dialog. The purchase orders that match the criteria you specified are displayed on the **Overview** FastTab.
1. On the **Overview** FastTab, enter the product receipt identifier in the **Product receipt** column for each purchase order in the grid. This information enables the system to post the product receipt.

    You must specify a product receipt identifier when each product is received. It's typically a reference to the packing slip from the supplier. This identifier is required for accounting because it enables supplier packing slips to be checked against what was received and against the accounted inventory or expense.

1. Select **Batch** to open the **Batch processing** dialog, where you can set up the [batch job](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) that posts the product receipt.

1. Select **OK** to return to the **Posting product receipt** dialog.
1. Select **OK** to close the **Posting product receipt** dialog.

After the system finishes processing product receipts for all lines in the purchase order, it sets the purchase order status to *Received* to indicate that the invoice can now be processed for the order.

To correct or cancel a product receipt, follow these steps:

1. Go to **Procurement and sourcing** \> **Purchase orders** \> **Receiving Products** \> **Product receipt**. The **Product receipt journal** page opens.
1. On the **Overview** tab, select the product receipt that you want to correct or cancel.
1. On the **Overview** tab toolbar, select **Correct** to make corrections or **Cancel** to cancel the product receipt.

> [!NOTE]
>
> - When correcting a product receipt, you can only reduce the received quantity. To raise the quantity, you must post a new product receipt journal.
> - Late selection isn't supported for product receipt posting. A product receipt number is required when you post a packing slip, but when you use late selection, this number isn't available because no parameter table exists and the system doesn't create an interaction during batch recurrence processing. Therefore, late selection is disabled for packing slip posting to ensure successful batch processing.

## Auto post product receipts when using WMS

Auto posting works differently if you're using warehouse management processes (WMS). Learn more in [Warehouse handling of inbound loads for purchase and inbound shipment orders](../warehousing/inbound-load-handling.md).

## Related information

- [Warehouse handling of inbound loads for purchase and inbound shipment orders](../warehousing/inbound-load-handling.md)
- [Purchase order overview](purchase-order-overview.md)
- [Create purchase orders](purchase-order-creation.md)
- [Approve and confirm purchase orders](purchase-order-approval-confirmation.md)
- [Overview of vendor invoices](../../finance/accounts-payable/vendor-invoices-overview.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
