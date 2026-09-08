---
title: Purchase order overview
description: Learn about purchase orders (POs) and links to other articles that are related to the various stages that a PO goes through.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form: PurchTable, PurchTablePart, PurchLineOpenOrder, PurchConfirmationRequestJournal
ms.topic: how-to
ms.date: 09/08/2026
ms.custom:
  - bap-template
---

# Purchase order overview

[!INCLUDE [banner](../includes/banner.md)]

This article provides general information about purchase orders (POs) and links to other articles that are related to the various stages that a PO goes through.

A purchase order (PO) is a document that represents an agreement with a vendor to buy goods or services. The document also helps keep track of product receipts that are made toward the order and, later, the accounting of vendor invoices that the vendor bills toward the order.

The **Purchase orders** page contains an overview of the available orders and lets you modify those orders. When you open a PO, you can select the **Header** view, which contains information that is specified only one time for each PO, such as the vendor details. Alternatively, you can select the **Lines** view, where you can modify order lines. Typically, you'll switch between these two views as you modify POs. Charges aren't listed directly on the **Purchase orders** page, but are accessed via menus on the order header and lines.

There are many reports where you can view information about POs, product receipts, and vendor invoices. These reports are found in the **Procurement and sourcing** and **Accounts payable** modules.

The **Purchase order preparation** and **Purchase order receipt and follow-up** workspaces let you view lists of POs in the various states that they've progressed to. They also provide a summary of the actions that must be taken. The **Purchase order preparation** workspace is focused on PO creation and review, processing of the order through approval, and confirmation with the vendor. The **Purchase order receipt and follow-up** workspace is focused on processing the receipt of goods or services against POs. It includes lists that give insight into receipts that are overdue, or that will soon be due for delivery by the supplier. These workspaces aren't used to perform the related receipt activities that are done in the warehouse. Those activities are performed by using pages in the **Inventory management** and **Warehouse management** modules. Processing of vendor invoices should be done by using the **Vendor invoice entry** workspace, and payments should be done by using the **Vendor payments** workspace.

The following articles provide an overview of the various stages that a PO goes through:

- [Create purchase orders](purchase-order-creation.md)
- [Approve and confirm purchase orders](purchase-order-approval-confirmation.md)
- [Product receipt against purchase orders](product-receipt-against-purchase-orders.md)
- [Overview of vendor invoices](../../finance/accounts-payable/vendor-invoices-overview.md)

## Types of purchase orders

There are three types of purchase orders. When you create a purchase order, you must specify the type. Set up a default order type for new orders on the **Procurement and sourcing parameters** page.

| PO type | Description |
|---|---|
| Journal | Use this type to create a draft order. This type doesn't affect stock quantities or generate inventory transactions. The PO journal lines aren't included in master scheduling. |
| Purchase order | Use this type to create purchase orders when you confirm orders with a vendor, and as the orders are processed through receipt and invoicing before payment is made to the vendor. This type of purchase order is the most common. |
| Returned order | Use this type when you return goods to the vendor. This type of order requires that you specify the return material authorization (RMA) number that the vendor gives you. Specify the RMA number on the **General** tab of the purchase order. The order lines must have negative quantities. |

## Purchase order data entities

If you integrate purchase orders with external systems through [OData](../../fin-ops-core/dev-itpro/data-entities/odata.md) or the [Data management framework](../../fin-ops-core/dev-itpro/data-entities/data-entities.md), be aware of which purchase order types each standard data entity covers.

The *Purchase order headers V2* (`PurchPurchaseOrderHeaderV2Entity`) and *Purchase order lines V2* (`PurchPurchaseOrderLineV2Entity`) data entities include only records where the purchase order type is *Purchase order*. By design, they don't return *Returned order* records. Therefore, queries against these entities don't include purchase return orders, and you can't create or update purchase return orders through them.

There's currently no separate standard public data entity for purchase return order headers and lines.

If your integration must read or write purchase return orders, use the [extensibility model](../../fin-ops-core/dev-itpro/extensibility/extensibility-home-page.md) to create a custom data entity that exposes the header and line data that you require. Before you use a custom entity in production, test its validations, table relations, cross-company behavior, and create and update operations.

> [!IMPORTANT]
> Don't modify the generated SQL view behind a standard data entity, and don't change the application database directly. These approaches bypass supported application validation, and your changes can be overwritten when the database is synchronized.

## Purchase order statuses

POs include several status fields that indicate the progress of the order. You can see all these fields in the **Header** view of the order. You can also see some of these fields in the grid overview of all orders. The **Purchase order status** field shows the status for quantities on the order. The following values are available:

- *Open order* – Orders are created, and quantities are on order.
- *Received* – You received the full quantity on the order, but you didn't invoice it yet.
- *Invoiced* – You invoiced the full quantity on the order. If an order is partially received or invoiced, *Received* status and *Invoiced* status aren't appropriate. Therefore, the order still has a status of *Open order*.
- *Canceled* – You confirmed an order but later canceled it. Therefore, this status indicates that there are no longer any open quantities on order.

The **Document status** field helps you quickly review the order's progress in terms of documents that are processed. It shows the status of the most recent document that is completed for the order. The following values are available:

- *None* – No document is processed for the order yet.
- *Purchase inquiry* – The system generated a purchase inquiry, and the order is awaiting feedback from the vendor.
- *Purchase order* – The system processed confirmation of the order.
- *Product receipt* – The system processed product receipt on the order.
- *Invoice* – The system accounted an invoice with the order.

Use the **Approval status** field when a PO goes through a review process or workflow. The following values are available:

- *Draft*, *In review*, and *Rejected* – These statuses are used only when an approval workflow is used for the PO.
- *Approved* – This status is assigned to orders that have completed workflow approval. Orders that are created without using an approval workflow receive a status of *Approved* immediately.
- *In external review* – This status is used in scenarios where a purchase inquiry is sent to the vendor, so that the vendor can confirm terms of the PO. This status is also used in the process that is initiated by the **Confirmation request** action. For this process, the vendor is asked to confirm terms of the PO by connecting to your system and registering whether it confirms or rejects the order.
- *Confirmed* – This status is assigned after the order has been confirmed. Typically, this status is the last approval status that is assigned to an order.

## Related information

- [Create purchase orders](purchase-order-creation.md)
- [Approve and confirm purchase orders](purchase-order-approval-confirmation.md)
- [Product receipt against purchase orders](product-receipt-against-purchase-orders.md)
- [Overview of vendor invoices](../../finance/accounts-payable/vendor-invoices-overview.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
