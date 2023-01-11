---
title: Purchase order overview
description: This article provides general information about purchase orders (POs) and links to other articles that are related to the various stages that a PO goes through.
author: GalynaFedorova
ms.author: gfedorova
ms.reviewer: kamaybac
ms.search.form: PurchTable, PurchTablePart, PurchLineOpenOrder, PurchConfirmationRequestJournal
ms.topic: overview
ms.date: 01/09/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Purchase order overview

[!include [banner](../includes/banner.md)]

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

There are three types of POs. When you create a PO, you must specify the type. You can set up a default order type for new orders on the **Procurement and sourcing parameters** page.

| PO type | Description |
|---|---|
| Journal | Use this type to create a draft order. This type doesn't affect stock quantities or generate inventory transactions. The PO journal lines aren't included in master scheduling. |
| Purchase order | Use this type to create POs when orders are confirmed with a vendor, and as the orders are processed through receipt and invoicing before payment is made to the vendor. This type of PO is the most common. |
| Returned order | Use this type when you return goods to the vendor. This type of order requires that you specify the return material authorization (RMA) number that the vendor gives you. You specify the RMA number on the **General** tab of the PO. The order lines must have negative quantities. |

## Purchase order statuses

POs include several status fields that indicate the progress of the order. All these fields are visible in the **Header** view of the order, and a few of them are also visible in the grid overview of all orders. The **Purchase order status** field shows the status for quantities on the order. The following values are available:

- *Open order* – Orders have been created, and quantities are on order.
- *Received* – The full quantity on the order has been received, but they haven't been invoiced yet.
- *Invoiced* – The full quantity on the order has been invoiced. If an order has been partially received or invoiced, then neither *Received* status nor *Invoiced* status is appropriate. Therefore, the order will still have a status of *Open order*.
- *Canceled* – An order was confirmed but later canceled. Therefore, this status indicates that there are no longer any open quantities on order.

The **Document status** field helps you quickly review the order's progress in terms of documents that have been processed. It shows the status of the most recent document that has been completed for the order. The following values are available:

- *None* – No document has been processed for the order yet.
- *Purchase inquiry* – A purchase inquiry has been generated, and the order is awaiting feedback from the vendor.
- *Purchase order* – Confirmation has been processed on the order.
- *Product receipt* – Product receipt has been processed on the order.
- *Invoice* – An invoice has been accounted with the order.

The **Approval status** field is used when a PO goes through a review process or workflow. The following values are available:

- *Draft*, *In review*, and *Rejected* – These statuses are used only when an approval workflow is used for the PO.
- *Approved* – This status is assigned to orders that have completed workflow approval. Orders that are created without using an approval workflow receive a status of *Approved* immediately.
- *In external review* – This status is used in scenarios where a purchase inquiry is sent to the vendor, so that the vendor can confirm terms of the PO. This status is also used in the process that is initiated by the **Confirmation request** action. For this process, the vendor is asked to confirm terms of the PO by connecting to your system and registering whether it confirms or rejects the order.
- *Confirmed* – This status is assigned after the order has been confirmed. Typically, this status is the last approval status that is assigned to an order.

## Additional resources

- [Create purchase orders](purchase-order-creation.md)
- [Approve and confirm purchase orders](purchase-order-approval-confirmation.md)
- [Product receipt against purchase orders](product-receipt-against-purchase-orders.md)
- [Overview of vendor invoices](../../finance/accounts-payable/vendor-invoices-overview.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
