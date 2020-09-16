---
# required metadata

title: Troubleshoot procurement and sourcing workflows
description: This topic describes how to fix issues that you might encounter while working with procurement and sourcing workflows.
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

This topic describes how to fix common issues that you might encounter while working with procurement and sourcing workflows.

## Changes to a purchase order are only allowed in draft state because change management is activated

This issue only occurs if the purchase order had a *Confirmed* state before requesting changes. If you request changes while the purchase order had an *Approved* state, then the workflow can be processed successfully.

### Reproduce the issue

One way to reproduce this issue is do the following:

1. Create and activate a purchase order workflow and a purchase order line workflow.
1. Enable change management for purchase orders by going to **Procurement and Sourcing > Setup > Procurement** and the setting **Sourcing parameter** to *Yes*.
1. Go to **Accounts Payable > All purchase orders > purchase order**.
1. Create a new purchase order with a purchase order line.
1. Submit the workflow.
1. Approve the workflow from the line level, so that it is approved and completed. The purchase order is also approved at this point.
1. Confirm the purchase order.
1. Select **Request change**.
1. Select **Update line** and then **Delivery remainder**.
1. Change the **Delivery remainder** value.
1. Submit it back to the workflow.
1. Check the workflow purchase order line history.
1. The workflow error occurs.

### Error description

The following error occurs in the workflow when a purchase order is resubmitted after a request change:

> Stopped (error): X++ Exception: Changes to purchase order PO0000569 are only allowed in state Draft when change management is activated at<br>
SysWorkflowParticipantProvider-resolve<br>
SysWorkflowParticipantProvider-resolveParticipants<br>
SysWorkflowServiceProvider-resolveParticipant<br>
SysWorkflowQueue-resume

### Issue fix

This is an issue that could occur due to inconsistency in purchase order distributions.

To unblock this issue and reset the purchase order to a *Draft* state, go to **Procurement and sourcing > Periodic tasks > Clean up > Purchase order distribution reset**. For more information, see the blog post [Resolve PO distribution errors in Dynamics 365 Supply Chain Management](https://cloudblogs.microsoft.com/dynamics365/it/2020/08/12/resolve-po-distribution-errors-in-dynamics-365-supply-chain-management/).

The issue will be resolved with [this KB Article](https://msdyneng.visualstudio.com/FinOps/_workitems/edit/467138).

## One or more accounting distributions is either over-distributed or under-distributed

This issue can occur due to inconsistency in purchase order distributions.

It is possible to unblock this issue and reset the purchase order to a *Draft* state using **Procurement and sourcing > Periodic tasks > Clean up > Purchase order distribution reset**. More information: [Resolve PO distribution errors in Dynamics 365 Supply Chain Management](https://cloudblogs.microsoft.com/dynamics365/it/2020/08/12/resolve-po-distribution-errors-in-dynamics-365-supply-chain-management/).

## On cancelling a delivery remainder on a purchase order with change management enabled, the purchase order changes a confirmed state

### Issue description

For a purchase order under change management, when a requested change is "just" to cancel a delivery remainder on the line(s), the purchase order will, when it is approved, go directly to a *Confirmed* state and no journal is created.

### Issue fix

Cancelling the delivery remainder doesn't influence the contents of the confirmation journal. This functionality should be used when the line has been partially received and the remainder quality is to be cancelled in the process step after the purchase order has been confirmed with the vendor.

If this should be reflected on the purchase order confirmation, the quantity should either be adjusted on the purchase order line, which will require a confirmation, or (if nothing have been received on the line) it can be removed and a reconfirmation will be required.

## Cancelled purchase orders appear in the draft list in the purchase order preparation workspace

### Issue description

After cancelling purchase orders that were in a *Confirmed* state, the cancelled purchase orders still appear in the list of draft purchase orders in the **Purchase order preparation** workspace.

### Issue fix

This happens only for purchase orders that are under change management because the cancellation is seen as a change that needs to be approved. The approval can be done automatically by the system. Therefore, the process is to submit the cancelled purchase order to the approval workflow so that it can get into an *Approved* state. Once this is done, the purchase order will not appear in the list of draft purchase orders in the **Purchase order preparation** workspace.

## Additional resources

[Get started with Procurement workflows](procurement-sourcing-workflows.md)