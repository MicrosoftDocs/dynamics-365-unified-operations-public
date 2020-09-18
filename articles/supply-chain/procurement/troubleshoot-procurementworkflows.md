---
# required metadata

title: Troubleshoot procurement and sourcing workflows
description: This topic describes how to fix issues that you might encounter while you work with procurement and sourcing workflows.
author: SmithaNataraj
manager: tfehr
ms.date: 09/16/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: PurchTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: smnatara
ms.search.validFrom: 2020-9-16
ms.dyn365.ops.version: Release 10.0.14

---
# Troubleshoot procurement and sourcing workflows

This topic describes how to fix issues that you might encounter while you work with procurement and sourcing workflows.

## Because change management is turned on, changes to a purchase order are allowed only in a Draft state.

This issue occurs only if the purchase order was in a *Confirmed* state before you requested changes. If you request changes while the purchase order is in an *Approved* state, the workflow can be processed successfully.

### Error description

The following error occurs in the workflow when a purchase order is resubmitted after a request change:

> Stopped (error): X++ Exception: Changes to purchase order PO0000569 are only allowed in state Draft when change management is activated at<br>
SysWorkflowParticipantProvider-resolve<br>
SysWorkflowParticipantProvider-resolveParticipants<br>
SysWorkflowServiceProvider-resolveParticipant<br>
SysWorkflowQueue-resume

### Reproduce the issue

The following procedure shows one way to reproduce the issue.

1. Create and activate a purchase order workflow and a purchase order line workflow.
1. Turn on change management for purchase orders by going to **Procurement and Sourcing \> Setup \> Procurement** and setting the **Sourcing parameter** option to *Yes*.
1. Go to **Accounts payable \> All purchase orders \> purchase order**.
1. Create a purchase order that has a purchase order line.
1. Submit the workflow.
1. Approve the workflow from the line level, so that it's approved and completed. At this point, the purchase order is also approved.
1. Confirm the purchase order.
1. Select **Request change**.
1. Select **Update line** and then **Delivery remainder**.
1. Change the **Delivery remainder** value.
1. Submit it back to the workflow.
1. Check the workflow purchase order line history.
1. Notice that the workflow error occurs.

### Issue resolution

This issue can occur because of inconsistency in purchase order distributions.

To unblock this issue and reset the purchase order to a *Draft* state, go to **Procurement and sourcing \> Periodic tasks \> Clean up \> Purchase order distribution reset**. For more information, see the following blog post: [Resolve PO distribution errors in Dynamics 365 Supply Chain Management](https://cloudblogs.microsoft.com/dynamics365/it/2020/08/12/resolve-po-distribution-errors-in-dynamics-365-supply-chain-management/).

The issue will be fixed through [this Microsoft Knowledge Base (KB) article](https://msdyneng.visualstudio.com/FinOps/_workitems/edit/467138).

## One or more accounting distributions are either over-distributed or under-distributed.

This issue can occur because of inconsistency in purchase order distributions.

To unblock this issue and reset the purchase order to a *Draft* state, go to **Procurement and sourcing \> Periodic tasks \> Clean up \> Purchase order distribution reset**. For more information, see the following blog post: [Resolve PO distribution errors in Dynamics 365 Supply Chain Management](https://cloudblogs.microsoft.com/dynamics365/it/2020/08/12/resolve-po-distribution-errors-in-dynamics-365-supply-chain-management/).

## If a delivery remainder is canceled on a purchase order where change management is turned on, the purchase order goes to a Confirmed state.

### Issue description

For a purchase order that is subject to change management, if the only change that is requested is the cancellation of a delivery remainder on one or more of the lines, the purchase order will go directly to a *Confirmed* state when it's approved, and no journal will be created.

### Issue resolution

Cancellation of a delivery remainder doesn't affect the contents of the confirmation journal. This functionality should be used when the line has been partially received, and the remainder quality should be canceled in the process step after the purchase order has been confirmed with the vendor.

If this should be reflected on the purchase order confirmation, the quantity should be adjusted on the purchase order line. In this case, confirmation will be required. Alternatively, if nothing has been received on the line, the quantity can be removed. In this case, reconfirmation will be required.

## Canceled purchase orders appear in the draft list in the Purchase order preparation workspace.

### Issue description

After you cancel purchase orders that were in a *Confirmed* state, the canceled purchase orders still appear in the list of draft purchase orders in the **Purchase order preparation** workspace.

### Issue resolution

This issue occurs only for purchase orders that are subject to change management. It occurs because the cancellation is considered a change that must be approved. The approval can be done automatically by the system. Therefore, the process is to submit the canceled purchase order to the approval workflow so that it can go to an *Approved* state. At that point, the purchase order will no longer appear in the list of draft purchase orders in the **Purchase order preparation** workspace.

## Additional resources

[Get started with Procurement workflows](procurement-sourcing-workflows.md)
