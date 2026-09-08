---
title: Approve and confirm purchase orders
description: Learn about the statuses that a purchase order goes through after it has been created, and the effect of enabling change management on POs.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form: PurchTable, PurchTablePart, PurchOrderInReview, PurchOrderApproved, PurchOrderInDraft, PurchOrderAssignedToMe, VendPurchOrderJournalListPage, PurchTableWorkflowDropDialog, VendPurchOrderJournal
ms.topic: how-to
ms.date: 09/08/2026
ms.custom:
  - bap-template
---

# Approve and confirm purchase orders

[!INCLUDE [banner](../includes/banner.md)]

This article describes the statuses that a purchase order (PO) goes through after you create it, and the effect of enabling change management on POs.

After you create a PO, it might need to go through an approval process. After the vendor agrees to the order, set the PO to a status of *Confirmed*.

## Approval of purchase orders

POs that don't use change management have a status of *Approved* as soon as you create them, whereas POs that use change management have a status of *Draft* when you first create them. A PO that you create by firming a planned order from master planning is always set to a status of *Approved*, regardless of the change management settings. A PO creates inventory transactions only when it reaches the *Approved* status. Therefore, that inventory doesn't appear as available for reservation or marking until the order is accepted.

Enable change management for POs by setting the **Activate change management** option on the **Procurement and sourcing parameters** page. When you enable change management, POs must go through an approval workflow after you complete them. Supply Chain Management has a workflow process editor where you can define a workflow to represent your approval process. This workflow can include rules for automatic approval, rules that determine who will be assigned to approve particular POs, and rules for escalating a workflow that has been waiting for approval for a long time. You can enable the change management process for all vendors or for specific vendors. You can also set up the process so that it can be overridden for individual POs.

When you enable change management, POs move through six approval statuses, from *Draft* to *Finalized*. After an order is approved, users who want to modify it must use the **Request change** action.

| Approval status | Description                                                                      | Request change is enabled |
|-----------------|----------------------------------------------------------------------------------|---------------------------|
| Draft           | The PO is a draft and hasn't been submitted for approval in the PO workflow.     | No                        |
| In review       | The PO was submitted for approval in the PO workflow. Approval is pending.       | No                        |
| Rejected        | The PO was rejected during the approval process.                                 | No                        |
| Approved        | The PO was approved.                                                             | Yes                       |
| Confirmed       | The PO was confirmed. A PO can't be confirmed until it has been approved.        | Yes                       |
| Finalized       | The PO was made final. It's now financially closed and can no longer be changed. | No                        |

## Confirming purchase orders

POs that have an approval status of *Approved* can go through additional steps before they're confirmed. For example, you might have to send a purchase inquiry to the vendor to inquire about prices, discounts, or receipt dates. In this case, you can set the PO to the *In external review* status by using the **Purchase inquiry** action.

Vendors that are set up to use the vendor collaboration interface can review orders on the portal, and approve or reject them. During this review process, the PO has a status of *In external review*. The vendor collaboration interface can be configured so that a confirmation from the vendor automatically confirms the order in Supply Chain Management. In this scenario, you must schedule the **Confirm accepted purchase orders from vendor collaboration** batch job, which is responsible for processing and confirming your POs. Alternatively, you can manually confirm a PO after you receive confirmation from the vendor. If a vendor rejects a PO, the rejection is received together with the reason for the rejection and suggestions for changes. In this case, the status of the PO remains *In external review*.

There's also an option to generate a pro-forma confirmation for an order before the actual confirmation has been processed. This option just creates a report that you can share with the vendor. It doesn't create any journal information.

After the vendor has agreed to the order, the next step is to record the PO as committed. You can complete this step by using either the **Confirmation** action or the **Confirm** action. Both these actions set the approval status of the order to *Confirmed*. Confirmation of an order initiates two additional processes:

- A journal is created to store an exact copy of what was confirmed in the system. Sometimes, orders require changes, and additional journals are created after the updated order is confirmed. These journals let you view the history of the various versions of the order that were confirmed.
- Accounting distributions are created, and order checks and budget checks occur if this functionality has been enabled. If either check fails, you receive an error message that states that changes must be made to the PO before it can be confirmed again.

> [!NOTE]
> The purchase order confirmation report includes price and amount information—the **Unit price**, **Discount**, **Discount percent**, and **Amount** columns, together with the totals table—only when the vendor is set up to include that information. This behavior is controlled by the **Purchase order prices/amount** option on the vendor record. The system applies this option when it creates the purchase order confirmation. Therefore, if you change the option on the vendor after an order was already confirmed, the confirmation that was already generated isn't affected. If you change the setting, confirm the purchase order again to generate a new confirmation report. (You don't have to delete the earlier confirmation.) The **Purchase order prices/amount** field on the **General** tab of the **Procurement and sourcing parameters** page sets the default value for newly created vendors only. It doesn't change existing vendors or existing confirmations.

A vendor might request some type of assurance that payment will be provided for a purchase. There are various methods for providing this guarantee within accounts payable processes. For example, the **Prepayment** action reserves funds for the PO, and this prepayment is recorded on the PO.

## Changing purchase orders

In some situations, you might have to change a PO after it has reached an approval status of *Approved* or *Confirmed*.

If the PO was created by using a change management process, you can make changes by recalling the order or, if the order has already been approved, by using the **Request change** action. In this case, the approval status is changed back to *Draft*, and you can then modify the order. After you've finished making changes, you might have to submit the PO for reapproval. You can configure the types of changes that require reapproval by using a **Re-approval rule for purchase orders** policy rule on the **Purchasing policies** page.

If part of the ordered quantity for a PO line has been delivered, you can't change the ordered quantity when the purchase order is in *Draft*. However, you can change the **Deliver remainder** quantity on the line for the purchase order that is in *Draft* status.

After an order has been confirmed, you can no longer delete it. However, you can cancel the total quantity or any remaining quantity on an order, provided that the quantity hasn't been received or invoiced. You can then use the **Finalize** action to prevent further processing.

## Canceling purchase orders

Use the **Cancel** action on the header to cancel a purchase order (PO).

If the quantity is partially registered, received, or invoiced, you can cancel only the remaining quantity that isn't registered, received, or invoiced. The order quantity is reduced accordingly. When you update the quantity on the line, you also update the line status. For example, the original quantity on the line is 5, and you receive a quantity of three. In this case, you can cancel only two. The line updates to *Received* status.

If you add a delivery remainder to the order line and it exceeds the quantity on the order line, the **Cancel** action doesn't cancel the excess quantity. Instead, the line remains in *Open order* status because it has a remaining quantity. For example, the original quantity on the line is 5, and the delivery remainder is 7. If you cancel the order, you cancel five, and a quantity of two remains, as you can see in the inventory transactions.

To cancel the whole quantity on a PO line, cancel the delivery remainder quantity on the line. The line updates to *Canceled* status.

If a PO is under change management, you must submit any change, such as cancellation of the order or the delivery remainder, to the workflow system for approval before the process can be completed and the inventory transactions can be updated as canceled.

## Related information

- [Purchase order overview](purchase-order-overview.md)
- [Create purchase orders](purchase-order-creation.md)
- [Product receipt against purchase orders](product-receipt-against-purchase-orders.md)
- [Vendor invoices overview](../../finance/accounts-payable/vendor-invoices-overview.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
