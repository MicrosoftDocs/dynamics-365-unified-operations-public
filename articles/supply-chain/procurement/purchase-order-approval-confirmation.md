---
# required metadata

title: Approve and confirm purchase orders
description: This article describes the statuses that a purchase order (PO) goes through after it has been created, and the effect of enabling change management on POs.
author: FrankDahl
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: PurchTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: yuyus


ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations, Retail

# ms.tgt_pltfrm: 
ms.custom: 93143
ms.assetid: cd12a944-c52c-4579-a301-7abe1d237c72
ms.search.region: Global
# ms.search.industry: 
ms.author: fdahl
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Approve and confirm purchase orders

[!include[banner](../includes/banner.md)]

[!include[retail name](../includes/retail-name.md)]

This article describes the statuses that a purchase order (PO) goes through after it has been created, and the effect of enabling change management on POs.

After a purchase order (PO) has been created, it might have to go through an approval process. After the vendor has agreed to the order, the PO is set to a status of **Confirmed**.

## Approval of purchase orders
POs that don’t use change management have a status of **Approved** as soon as they are created, whereas POs that use change management have a status of **Draft** when they are first created. A PO that has been created by firming a planned order from master planning is always set to a status of **Approved**, regardless of the change management settings. A PO creates inventory transactions only when it reaches the **Approved** status. Therefore, that inventory doesn’t appear as available for reservation or marking until the order is accepted.  

You enable change management for POs by setting the **Activate change management** option on the **Procurement and sourcing parameters** page. When change management is enabled, POs must go through an approval workflow after they have been completed. Microsoft Dynamics 365 for Finance and Operations has a workflow process editor where you can define a workflow to represent your approval process. This workflow can include rules for automatic approval, rules that determine who will be assigned to approve particular POs, and rules for escalating a workflow that has been waiting for approval for a long time. You can enable the change management process for all vendors or for specific vendors. You can also set up the process so that it can be overridden for individual POs.  

When change management is enabled, POs move through six approval statuses, from **Draft** to **Finalized**. After an order has been approved, users who want to modify it must use the **Request change** action.

| Approval status | Description                                                                      | Request change is enabled |
|-----------------|----------------------------------------------------------------------------------|---------------------------|
| Draft           | The PO is a draft and hasn’t been submitted for approval in the PO workflow.     | No                        |
| In review       | The PO was submitted for approval in the PO workflow. Approval is pending.       | No                        |
| Rejected        | The PO was rejected during the approval process.                                 | No                        |
| Approved        | The PO was approved.                                                             | Yes                       |
| Confirmed       | The PO was confirmed. A PO can’t be confirmed until it has been approved.        | Yes                       |
| Finalized       | The PO was made final. It’s now financially closed and can no longer be changed. | No                        |

## Confirming purchase orders
POs that have an approval status of **Approved** can go through additional steps before they are confirmed. For example, you might have to send a purchase inquiry to the vendor to inquire about prices, discounts, or delivery dates. In this case, you can set the PO to the **In external review** status by using the **Purchase inquiry** action.  

Vendors that are set up to use the Vendor portal can review orders on the portal, and approve or reject them. During this review process, the PO has a status of **In external review**. The Vendor portal can be configured so that a confirmation from the vendor automatically confirms the order in Finance and Operations. Alternatively, you can manually confirm a PO after you receive confirmation from the vendor. If a vendor rejects a PO, the rejection is received together with the reason for the rejection and suggestions for changes. In this case, the status of the PO remains **In external review**.  

There is also an option to generate a pro-forma confirmation for an order before the actual confirmation has been processed. This option just creates a report that you can share with the vendor. It doesn’t create any journal information.  

After the vendor has agreed to the order, the next step is to record the PO as committed. You can complete this step by using either the **Confirmation** action or the **Confirm** action. Both these actions set the approval status of the order to **Confirmed**. Confirmation of an order initiates two additional processes:

-   A journal is created to store an exact copy of what was confirmed in the system. Sometimes, orders require changes, and additional journals are created after the updated order is confirmed. These journals let you view the history of the various versions of the order that were confirmed.
-   Accounting distributions are created, and order checks and budget checks occur if this functionality has been enabled. If either check fails, you receive an error message that states that changes must be made to the PO before it can be confirmed again.

A vendor might request some type of assurance that payment will be provided for a purchase. There are various methods for providing this guarantee within accounts payable processes. For example, the **Prepayment** action reserves funds for the PO, and this prepayment is recorded on the PO.

## Changing purchase orders
In some situations, you might have to change a PO after it has reached an approval status of **Approved** or **Confirmed**.  

If the PO was created by using a change management process, you can make changes by recalling the order or, if the order has already been approved, by using the **Request change** action. In this case, the approval status is changed back to **Draft**, and you can then modify the order. After you’ve finished making changes, you might have to submit the PO for re-approval. You can configure the types of changes that require re-approval by using a **Re-approval rule for purchase orders** policy rule on the **Purchasing policies** page.  

If part of the ordered quantity for a PO line has been delivered, you can’t change the ordered quantity. However, you can change the **Deliver remainder** quantity on the line. You can then use the **Finalize** action to cancel lines and prevent further processing. 

After an order has been confirmed, you can no longer delete it. However, you can cancel the total quantity or any remaining quantity on an order, provided that the quantity hasn’t been received or invoiced.

See also
--------

[Purchase order overview](purchase-order-overview.md)

[Purchase order creation](purchase-order-creation.md)

[Product receipt against purchase orders](product-receipt-against-purchase-orders.md)

[Overview of vendor invoices](../../financials/accounts-payable/vendor-invoices-overview.md)



